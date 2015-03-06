# This week I learned about Sinon Matchers

<img src="/wp-content/uploads/dcneiner.jpg" width="45" class="float-left" />Editor's note: This is a guest post by <a href="https://github.com/dcneiner">Doug Neiner</a>. Doug is a Senior Software Engineer at <a href="http://leankit.com/">LeanKit</a>, and <a href="http://thechangelog.com/membership/">a supporting community member</a>. Each week we invite our <a href="http://thechangelog.com/membership/">community members</a> to share something they've learned in our member's Slack room and we choose someone's TWIL to post on the blog. This post originally appeared here on The Changelog <a href="https://github.com/thechangelog/draft/blob/master/published/sinon-matchers/post.md">#</a>.

<hr/>

I'm a huge fan of [Sinon](http://sinonjs.org/) for test spies, stubs, fake timers, etc – but I continually learn new things about it. *This week I learned* about [sinon matchers](http://sinonjs.org/docs/#matchers).

While some of us were pairing on a test case at LeanKit this week, we needed to verify part of an object passed into a method we were stubbing.

Previously, if we had to test something like this, we'd use the `args` on the stub:

```js
var stub = sinon.stub();
stub( "topicName", { other: "field", some: "object" } );

// In the test
stub.lastCall.args[0].should.equal( "topicName" );
stub.lastCall.args[1].some.should.equal( "object" );
```

It is much nicer to write using sinon's `calledWith` method, but this would fail since we are doing a partial match:

```js
// this test fails
stub.should.be.calledWith( "topicName", { some: "object" } );
```

_(We use [chai](http://chaijs.com/) and its `should` syntax with [sinon-chai](https://github.com/domenic/sinon-chai) to achieve this syntax.)_

However, now with sinon matchers, we can write the following and it will match the partial object:

```js
stub.should.be.calledWith( "topicName", sinon.match( { some: "object" } ) );
```

You can use `regexp`, `string` and other matchers as well including a custom function matcher and nested matchers. I can't wait to use these more in our tests going forward.

---

Tags: Sinon, Testing, TWIL
