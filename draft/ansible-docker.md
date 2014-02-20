# Why Ansible and Docker?

There is a lot of interest from the tech community in both [Docker](https://www.docker.io/) and
[Ansible](https://github.com/ansible/ansible), I am hoping that after reading this article you will share our enthusiasm. You will also gain a practical insight into using Ansible
and Docker for setting up a complete server environment for a Rails application.

Let me start by addressing the elephant in the room. Many reading this
might be asking, "Why don't you just use Heroku?" And the answer is because
I can run this on any host, with any provider. Because I prefer flexibility
over convenience. Because I can run anything in this manner, not just
web applications. Last but not least, because I am a tinkerer
at heart, I get a kick from understanding how all the pieces fit together.

## Why Ansible?

After 4 years of heavy Chef usage, the _infrastructure as code_
mentality becomes really tedious. I was spending most of my time with
the code that was managing my infrastructure, not with the
infrastructure itself. Any change, regardless how small, would require a
considerable amount of effort for a relatively small gain. With
[Ansible](http://ansible.com), there’s data describing infrastructure on
one hand, and the constraints of the interactions between various
components on the other hand. It’s a much simpler model that enables me
to get done a lot more by letting me focus on what makes my
infrastructure personal. Similar to the Unix model, Ansible provides
simple modules with a single responsibility that can be combined in
endless ways.

Ansible has no dependencies other than python and ssh. It doesn’t
require any agents to be set up on the remote hosts and it doesn’t leave
any traces after it runs either. What’s more, it comes with an
extensive, built-in library of modules for controlling everything from
package managers to cloud providers, to databases and everything else in
between.

## Why Docker?

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

## The Setup

Without leaving my terminal, I can have Ansible provision a new instance
for me with any of the following: Amazon Web Services, Linode, Rackspace
or DigitalOcean. To be more precise, I can have Ansible create a new
DigitalOcean 2GB droplet in Amsterdam 2 region in precisely 1 minute and
25 seconds. In a further 1 minute and 50 seconds I can have the system
setup with Docker and a few other personal preferences. Once I have this
base system in place, I can deploy my application.  Notice that I didn't
setup any database or programming language. Docker will handle all
application dependencies.

First, the application code will be cloned remotely from a git
repository. Since Ansible runs all remote commands via SSH, the keys in
my local agent will be forwarded with the session, no git credentials
will be cached or stored remotely.

## Docker and application dependencies

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
Redis 2.8 by including the following `.docker_container_dependencies`
file:

<pre>
gerhard/mysql:5.5
gerhard/redis:2.8
</pre>

The Ansible playbook will notice this file and will instruct Docker to
pull the correct images from the Docker index and start them as
containers. It also links these service containers to my application
container. If you want to find out more details about how Docker
container links work, refer to the [Docker 0.6.5
announcement](http://blog.docker.io/2013/10/docker-0-6-5-links-container-naming-advanced-port-redirects-host-integration/).

My application also comes with a Dockerfile which is specific about the
Ruby Docker image that is required. As this is already build, the steps
in my Dockerfile have the confidence that the correct Ruby version is
available to them.

<pre>
FROM howareyou/ruby:2.0.0-p353

ADD ./ /terrabox

RUN \
  . /.profile ;\
  rm -fr /terrabox/.git ;\
  cd /terrabox ;\
  bundle install --local ;\
  echo '. /.profile && cd /terrabox && RAILS_ENV=test bundle exec rake db:create db:migrate && bundle exec rspec' > /test ;\
# END RUN

CMD . /.profile && cd /terrabox && export RAILS_ENV=production && rake db:create db:migrate && foreman start web

EXPOSE 3000
</pre>

The first step is to copy all my application's code into the Docker
image and load the global environment variables added by previous
images. The Ruby image for example will append `PATH` configuration
which ensures that the correct Ruby binary gets loaded first. Next, I
remove the git history as this is not useful in the context of a Docker
container. I install all the gems and then create a `test` script which
will be run by the test-only container. The purpose of this is to have a
"canary" which ensures that the application and all its dependencies are
properly resolved, that the Docker containers are linked correctly and
all tests pass before the actual application container will be started.
The command that gets run when a new web application container gets
started can be seen in the `CMD` step. The last instruction in this
application's Dockerfile maps port 3000 from inside the container to an
automatically allocated port on the host that runs Docker. This is the
port that the reverse proxy or load balancer will use when proxying
public requests to my application.

## Time to setup an application with all its dependencies

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

## Conclusion

> Reader take-aways

I gave a talk at the January London Docker meetup on this subject, you
will [find the slides on
Speakerdeck](https://speakerdeck.com/gerhardlazu/ansible-and-docker-the-path-to-continuous-delivery-part-1).

If you want to be updated every week of articles like this one,
subscribe to [The Changelog Weekly](http://thechangelog.com/weekly/).
