If you have an application which you want to host yourself, Ansible and
Docker are the quickest way to do so. Ansible can create a new host (or
10) with either DigitalOcean, Amazon, Rackspace or Linode from your
terminal. It can setup all dependencies on this new host, then it can
get your application up and running, including all the dependent
services as a series of Docker containers with little effort on your
part.

Let me start by addressing the elephant in the room: why don't you just
use Heroku? Because I can run this on any host, with any provider.
Because I prefer flexibility over convenience and can run anything in
this manner, not just web applications. Last but not least, because I am
a tinkerer at heart, I get a kick from understanding how pieces fit
together.

So why [Ansible](http://ansible.com)? After 4 years of heavy Chef usage,
the “infrastructure as code” mentality becomes really tedious. I was
spending most of my time with the code that was managing my
infrastructure, not with the infrastructure itself. Any change,
regardless how small, would require a considerable amount of effort for
a relatively small gain. With Ansible, there’s data describing
infrastructure on one hand, and the constraints of the interactions
between various components on the other hand. It’s a much simpler model
that enables me to get done a lot more by letting me focus on what makes
my infrastructure personal. Similar to the Unix model, Ansible provides
simple modules with a single responsibility that can be combined in
endless ways.

[Docker](http://docker.io) is establishing itself as the most reliable
and convenient way of deploying a process on a host. This can be
anything from mysqld to redis, to a Rails application. Just like git
snapshots and distributes code in the most efficient way, Docker does
the same for processes. It guarantees that everything required to run
that process will be available regardless of the host that it runs on.
Processeses now have a social side, they always come with friends, ready
for action.

A common but understandable mistake is to treat a Docker container as a
VM. The [Single Responsibility
Principle](http://en.wikipedia.org/wiki/Single_responsibility_principle)
still applies, running a single process per container will give it a
single reason to change, it will make it re-usable and easy to reason
about. This model has stood the test of time in the form of the Unix
philosophy, it makes for a solid foundation to build on.

So what are the steps that I expect to happen once I have a new host
with docker set up?

First, the application code will be cloned remotely from a git
repository. Since Ansible runs all remote commands via SSH, the keys in
my local agent will be forwarded with the session, no git credentials
will be cached or stored remotely. 

I find it perplexing that most developers are specific about the version
of the programming language which their application needs, the version
of the dependencies in the form of Python packages, Ruby gems or node.js
modules, but when it comes to something as important as the database or
the message queue, they just use whatever is available in the
environment that the application runs. I believe this is one of the
reasons behind the devops movement, developers taking responsibility for
the application's environment. Docker makes this task easier and more
straightforward by adding a layer of pragmatism and confidence to the
existing practices.

My application defines dependencies on processes such as MySQL 5.5 and
Redis 2.8 by containing empty `.docker_mysql-5.5` and
`.docker_redis-2.8` files. It's a simplistic but efficient approach
which proved sufficient. My Ansible playbook will notice these files and
will instruct Docker to pull the correct images from the Docker index
and start them as containers. My application also comes with a
Dockerfile which is specific about the Ruby Docker image that is
required. The Dockerfile contains all the steps required to produce a
runnable Docker image for my application. Every step in a Dockerfile
creates a new layer which will be used by the next step. Next time the
same step needs to run, the resulting image (layer) will be used
instead.

As my application image is being built, it installs all the required
Ruby gems, it creates a MySQL database in the MySQL server which runs as
a separate Docker container, migrates the MySQL database and then runs
the test suite. If everything passes, I will have my application
packaged as a Docker image, ready to be started as a Docker container.

For a medium-sized Rails application, with about 100 gems and just as
many integration tests running under Rails, this takes 8 minutes and 16
seconds on a 2GB and 2 core instance, without any local Docker images.
If I already had the images on that host, this would drop to 4 minutes
and 45 seconds. Furthermore, if I had a master application image to base
a new image build of the same application, this would drop to a mere 2
minutes and 23 seconds. To put this into perspective, it takes me just
over 2 minutes to deploy a new version of my Rails application,
including dependent services such as MySQL and Redis. This deploy also
includes a full test suite run which alone takes about a minute
end-to-end. Without intending, Docker became a simple Continuous
Integration environment that leaves test-only containers behind for
inspection when tests fail, or starts new application containers
containing the latest version of my application. All of a sudden, I can
validate new code with my customers in minutes, with the guarantee that
different versions of my application are isolated from one another, all
the way to the operating system. Unlike traditional VMs which take
minutes to start, a Docker container will take under a second.

> Another paragraph so that the ending isn't too abrupt.

If you want to find out more on the subject, see my slides from the
[January London Docker meetup](https://speakerdeck.com/gerhardlazu/ansible-and-docker-the-path-to-continuous-delivery-part-1).
