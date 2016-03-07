After listening to shows #185 and #189, both on APIs, I started realizing that perhaps there still isn't one central resource for learning about REST APIs. So, I've put together this essential reading list for those of you looking for some of the best resources out there on RESTful APIs.

[Objects at REST, Part 1: What Is It?](https://medium.com/@Stuart_Weir/objects-at-rest-part-1-what-is-it-3e26f0978616#.rr8x0ahz0)
This was written recently by me, describing (in one post) many of the fundamental principles, terminology, and ideas behind RESTful APIs. While it's not too granular, I goes into some detail about what REST APIs really are to build your understanding of the technology quickly.
> An API is an Application Programming Interface. This sounds super technical, but it actually really isn’t. It’s essentially an interface for programmers, much like a User Interface (UI) is an interface for product users.

[REST API Tutorial](http://www.restapitutorial.com/)
An excellent resource on REST APIs, REST API Tutorial offers a number of tutorials on REST, quick tips, HTTP method use,resource naming, and a number of other REST API best practices. A _must read_.
 
> Building RESTful web services, like other programming skills is part art, part science. As the Internet industry progresses, creating a REST API becomes more concrete with emerging best practices. As RESTful web services don't follow a prescribed standard except for HTTP, it's important to build your RESTful API in accordance with industry best practices to ease development and increase client adoption.

> Presently, there aren't a lot of REST API guides to help the lonely developer. RestApiTutorial.com is dedicated to tracking REST API best practices and making resources available to enable quick reference and self education for the development crafts-person. We'll discuss both the art and science of creating REST Web services.

> —Todd Fredrich, REST API Expert

[API Glossary](http://apiglossary.com/), by Mashape
The Changelog talked a lot about APIs with Ahmad Nassri from Mashape, and after taking a look at some of their free resources, I'm pretty convinced they're the King Kong of APIs. API Glossary is exactly what it sounds like: an open source API Glossary, contributed by Mashape and the larger open source community.
> Learn the lingo of Application Programming Interfaces and the acronyms, design patterns and tools that surround them.

[How REST Constraints Affect API Design](http://sookocheff.com/post/api/how-rest-constraints-affect-api-design/)
What can I say... after reading this article, I'm convinced Kevin is one of my favourite tech writers. How REST Constraints Affect API Design get's straight to the point: Kevin highlights some of REST's main principles, and how this changes the way an API is designed. One of my favourites!
> REST is defined by four interface constraints: identification of resources; manipulation of resources using representations; self-descriptive messages; and, hypermedia as the engine of application state.

> Why is this important for APIs?

> API design is in an infancy. Each API is designed for a single use case and standard. This proliferation of different design ideas results in APIs that each have their own specification and semantics. Interoperability between APIs is nonexistent. In the early 1990s the Web was facing this exact problem and as a result the principles of REST were formalized and adopted. The result was a scalable, resilient and ultimately successful system. By adopting the REST constraints in our APIs we can take advantage of this foundational work to provide APIs that form a scalable and resilient network of their own.

> We will take a look at each of the four interface constraints in turn and see how they can be used to design an API that developers love to use.

[REST - The Short Version](http://exyus.com/articles/rest-the-short-version/)
If you aren't entirely familiar with all of the terminology of APIs/HTTP/Web related technologies, this shouldn't be your first stop. However, REST - The Short Version is an excellent reference to make sure you're following RESTful principles.
> Getting a clear handle on the definition of the REST architectural style can be daunting. While there is no shortage of descriptions available, I did not find many of them helpful at first. Also, as I began talking about REST to colleagues, I often had a difficult time producing clear descriptions for the key points. Over time, however, I sharpened my summary into a version that seemed to make sense to most of my listeners. I offer here my rendition of the REST model.

[Choosing an HTTP Status Code - Stop Making It Hard](http://racksburg.com/choosing-an-http-status-code/)
A lot of people tend to just use the regular status codes, such as 200, 404, etc., but most often, your REST API needs more descriptive status codes. Michael Kropat helps you understand what different status codes mean, and where you should use them. It's also a very humourous article :)
> Life is bliss, well… until someone tells you you’re not doing this REST thing. Next thing you know, you can’t sleep at night because you need to know if your new resource returns the RFC-compliant, Roy-Fielding-approved status code. Is it just a 200 here? Or should it really be a 204 No Content? No, definitely a 202 Accepted… or is that a 201 Created?

[JSON API](http://jsonapi.org/)
In Podcast #189, Adam and Jerod talked to Yehuda Katz on JSON API, the JSON specification for building uniform, RESTful APIs. If you haven't taken a look yet, you should: Yehuda and the rest of the contributors to this project put in a lot of effort to bring you, in my opinion, some of the best conventions for handling JSON. If you like Ember.js or Rails, you'll probably like JSON API for its convention-over-configuration approach.
> If you've ever argued with your team about the way your JSON responses should be formatted, JSON API can be your anti-bikeshedding tool.

> By following shared conventions, you can increase productivity, take advantage of generalized tooling, and focus on what matters: your application.

> Clients built around JSON API are able to take advantage of its features around efficiently caching responses, sometimes eliminating network requests entirely.

[Awesome-API](https://github.com/Kikobeats/awesome-api)
For "everything else," take a look at Awesome API. Some of what it references is already in this list, but that just means it's more awesome ;) Once you understand the essentials of RESTful APIs, this is the go-to list for everything else, from Authentication, JSON Web Tokens, OAuth, Media Types, Testing, etc.
> A curated list of awesome resources for designing and implementing RESTful APIs.