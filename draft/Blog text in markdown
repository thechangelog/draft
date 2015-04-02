#title: How to make your open-source project thrive, with Andrey Petrov

===

##Abstract: Andrey Petrov ([@shazow](https://twitter.com/shazow)) spoke at last week's [Sourcegraph open-source meetup](http://www.meetup.com/Sourcegraph-Hacker-Meetup/) about lessons learned from his successes and "many failures" creating open-source projects. Andrey is author of the popular urllib3 library and several other popular open-source libraries on GitHub. During the day, he works at Briefmetrics and is also a YC alum, ex-Googler, and a cat person. He writes mostly in Python, JavaScript, and Go. 


**If you have the time, you should watch the full video of Andrey's awesome and hilarious talk.**

===

[Watch the video of Andrey's talk](https://youtu.be/ScUIlbHnxGI)

[Link to Andrey's slides](https://docs.google.com/presentation/d/13FtcUcurtKdq3UJ65-xlWo8C5S4v_xtCYa5C7-QhKgg/edit?usp=sharing)

===

####Why open source?
Andrey began the talk by outlining some of the key benefits of open source:

* It's a good way to get free, replicated backups of your code.
* It makes it easy to link to and ask for help.
* It helps give you a bigger footprint of influence in the programming world.
* It lets you get the most out of sunk costs.

You've invested a lot of time and effort into your code. Open-sourcing it makes it available and reusable. Employees come and go, as do companies, but open-source code will always be available to you and others who find it useful.

<script type="text/javascript" src="https://sourcegraph.com/github.com/shazow/urllib3/.PipPackage/urllib3/.def/urllib3/response/HTTPResponse/.sourcebox.js"></script>
**_A snippet from urllib3, a popular Python open-source library that Andrey created_**

Open-sourcing has many benefits, but there's a lot of open-source code out there already. How do you make your project stand out? Here's 4 steps you can use to build great open-source software.

####Step 1: Define what success looks like
Andrey's [urllib3](https://sourcegraph.com/shazow/urllib3), a HTTP library written in Python, is used by millions of people everyday, has 785 stars on GitHub, and has been growing since its creation in 2008. Andrey has another project, [ssh-chat](https://sourcegraph.com/shazow/ssh-chat), that has 1560 stars on GitHub, but is only used by ~15 people today. So which project is more "successful?" In order to answer that question, Andrey described how defining success at the beginning of project will help you understand if it's successful or not. 

The beginning of every open-source project looks like this:

1. Build something. Anything.
2. Get frustrated with the hardest parts, build libraries and tools to help.
3. Discard the original project to focus on the libraries, which become your new project.
4. Go back to step 2 and repeat.

The story of [urllib3](https://sourcegraph.com/shazow/urllib3) begins with the problem of trying to upload billions of images to S3 in 2008. Using existing Python libraries, this would have taken 3+ weeks because there was no good concurrency support. You could use s3funnel, a multithreaded S3 client, but managing threads is painful. You could use a worker pool in s3funnel, instead, but existing HTTP libraries didn't re-use connections and most solutions weren't threadsafe or lacked multipart (filepost) encoding. Enter [urllib3](https://sourcegraph.com/shazow/urllib3).

<script type="text/javascript" src="https://sourcegraph.com/github.com/shazow/urllib3/.PipPackage/urllib3/.def/dummyserver/handlers/TestingApp/encodingrequest/request/.sourcebox.js"></script>
**_A snippet of requests, a popular function in urllib3_**

In Andrey's words, "The solution space [in engineering] is about building something and solving a problem. For urllib3, the space was really small and the solution to other things were really useful, and that's what made it successful." 


**When defining a project's goals, think about how solving a small problem can make a large impact.**

Another form of "success" in open source is exemplified by ssh-chat, an encrypted chat-over-SSH program written in Go. Andrey started ssh-chat as a weekend project.  One of the main contributions to the project's success started with creating a thorough README. As Andrey puts it, "Having a great README is basically 80% of the work to success. You need to be able to answer three questions for your contributors: who else uses it, for what, and where I can get more help."

<script type="text/javascript" src="https://sourcegraph.com/github.com/shazow/ssh-chat/.GoPackage/github.com/shazow/ssh-chat/chat/.def/Command/Handler/.sourcebox.js"></script>
**_A snippet of ssh-chat, a popular ssh-chat program written in Go_**

But just creating an awesome README didn't kickstart the impressive growth of ssh-chat. To make it thrive, it needed more traction.

####Step 2: Recruit core contributors
"If you build it... they may not come" should be the rallying cry of all open source work. As proof of this, Andrey embedded a bounty in the code of one of his projects, promising $5 to anyone who issued a simple pull request to remove the file. As of today, no one has yet claimed the free money.

<image> "bounty"

To spread the word about ssh-chat, Andrey started asking for help, asking for improvements, and finding ways to bring more people into the project. In order to help build interest, Andrey reached out to people on Twitter and offered free Go programming lessons in exchange for opening pull requests. This overcame the initial inertia of getting a few people involved and interested in the project. These early contributors eventually became champions of ssh-chat and started answering questions on Stack Overflow.

Another component of building and maintaining open source projects is learning to be inclusive. "Accepting pull requests very generously, and very graciously" was a key step in building more community interest and is something that many open-source authors miss in the beginning. And asking specific people to make a pull request was much more effective than making more generalized asks of his Twitter followers. 

####Step 3: Market and promote your project
In general, programmers tend not to be self-promoting types, so actively marketing and promoting an open-source project doesn't come naturally. With this in mind, Andrey identified ways that programmers can promote their projects without being self-aggrandizing.

One approach is to write interesting blog posts about your projects to provide clearer context of the project's story and mission. [Medium](http://medium.com) is a great platform for sharing in the technology community and has more potential readers than a self-hosted blog. 

Other opportunities for connecting with contributors that worked for urllib3 and ssh-chat included:

1. Answer questions on Stack Overflow (set up alerts on Stack Overflow for specific topics)
2. Participate in discussions on Hacker News, reddit/r/programming, etc.
3. Sell to other open-source projects and establish partnerships with them. "The only reason urllib3 is the most popular third-party Python library today is because it's part of <a target="_blank" href="https://sourcegraph.com/github.com/kennethreitz/requests">requests</a>."
4. Feed the non-trolls: Getting upvotes on your announcement post is only half the equation. More activity and discussion yields more people clicking on it and more updates, so if you respond to almost every comment, then that's 2x as many comments. 

<image> "what would you rather click"


####Step 4: Profit?
"We want to be like Docker!" Don't we all?

Two things helped Docker develop into a widely adopted open-source project:

1. It's very well funded.
2. It has thousands of contributors helping for free.

One of the key insights behind Docker's success is that they didn't over-focus on the business model until the OSS project was insanely popular. So how can you replicate this? Enter the "corp'en source model"—where open source work becomes the core competency and business of a corporation. 


**The Corp'en source model**

Some of the most well-known companies that embrace corp-en source include:

1. Docker (via an open core)
2. Gratipay (via dogfooding their own product to receive revenue)
3. Nginx (via consulting and support)
4. Mozilla (via advertising)
5. GnuPG (via charity and grants)

**So how do you monetize your contributions as a free agent?**

Well, you don't. Not directly, at least. 

Despite widespread adoption of urllib3, Andrey shared that he only received $5 from a single user (which he appreciates!), proving that widespread adoption of a project does not necessarily provide a sustainable revenue model to justify the time and effort.

Some companies, like Stripe and Sourcegraph are sponsoring open-source work. Read more about these projects here:

 * [Stripe's open source retreat](https://medium.com/@shazow/urllib3-stripe-and-open-source-grants-edb9c0e46e82)
 * [Sourcegraph's open source fellowships](http://techcrunch.com/2014/02/15/with-hackathons-taking-center-stage-the-coming-transformation-of-the-computer-scientist/).

####Open source: just do it and do it right

Open source is incredibly valuable and rewarding, but to do it successfully, you gotta hustle.

In this case, much of the work that went into building urrlib3 meant focusing on a small, but common challenge, writing a great README, reaching out to people to contribute, and promoting the project through blog posts. It's also worth mentioning that it took some time for each of these projects to gain traction and Andrey's commitment to improving the project over time helped build his reputation and respect within the programming community.

In short, here's how to make an open source project thrive:

1. Define a small solution space that affects a lot of people.
2. Write a great README and recruit people who can and will help build it with you.
3. Market and promote the project with blog posts and social media activity.
4. Identify and reach out to companies who will benefit from your work.


[Link to Andrey's slides](https://docs.google.com/presentation/d/13FtcUcurtKdq3UJ65-xlWo8C5S4v_xtCYa5C7-QhKgg/edit?usp=sharing)

***For more from Andrey, follow him [@shazow](http://twitter.com/shazow) on Twitter or check out his Sourcegraph profile [shazow](https://sourcegraph.com/shazow), and be sure to check out his awesome projects, [urllib3](https://sourcegraph.com/shazow/urllib3) and [ssh-chat](https://sourcegraph.com/shazow/ssh-chat).***

***Special thanks to Andrey and his wife, Tracy Osborn, for making the long drive to give this talk! You can see Tracey talk about her new book on Django development in the meetup lightning talks on our [Sourcegraph YouTube channel](https://www.youtube.com/channel/UCOy2N25-AHqE43XupT9mwZQ/videos).***

***Want to see more talks like this in person? Sign up for our [Sourcegraph hacker meetup group](http://www.meetup.com/Sourcegraph-Hacker-Meetup/)!***

