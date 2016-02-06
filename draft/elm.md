# Elm, functional frontend development

## … and why you should care

A few months ago I learned of [Elm](http://elm-lang.org/), which claims to be "the best of functional programming in your browser". After inhaling the documentation and watching a few videos and talks, I started tinkering myself and quickly [fell in love with Elm](https://dennisreimann.de/articles/elm.html) and the feeling it gives me when writing code in it.

The last time I felt this excitement of working with something radically new was when I learned Rails – almost ten years ago. Back then one could feel that Rails would be a big shift, because it was a coherent package that bundled up web dev learnings, best practices, and some very nice ideas for its future development. Right now this is happening again with Elm, so let us have a look at what is exciting me …

### Functional is becoming a trend in frontend development

In 2015 functional (reactive) programming advanced in the frontend field and by now every frontend developer should have heard of it. Functional programming paradigms and ideas are influencing JavaScript and its frameworks: [PureScript](http://www.purescript.org/) and [RxJS](https://github.com/Reactive-Extensions/RxJS) are examples for languages and libraries that build on the functional-reactive concepts – [React](https://facebook.github.io/react/) and accompanying libraries are increasingly influenced by the functional trend as well.

But instead of mounting a framework for working in a functional manner on top of our good old JavaScript, Elm is a whole new language that builds on functional paradigms and makes reactive programming a core concept. And even so, it compiles to JavaScript so it can run in the browser. Elm does not try to bring functional programming to JavaScript, but _to its developers_.

### Statically typed, no more runtime errors.

As opposed to JavaScript, Elm is statically typed. The compiler type-checks the code and guarantees to generate reliable code that will not throw any runtime exceptions caused by inconsistent types or undefined variables. The compiler is the centerpiece of Elm and enables many of the interesting features like [very helpful error messages](http://elm-lang.org/blog/compiler-errors-for-humans) that also contain hints for fixing the code or a [package manager that enforces semver](http://elm-lang.org/blog/announce/package-manager) through code analysis.

Consequently, even the view is statically typed – the templates, which are written in [elm-html](https://github.com/evancz/elm-html), are based on the concept of the Virtual DOM, just like in React. Regarding the rendering, elm-html [performs even better than React](http://elm-lang.org/blog/blazing-fast-html) and other JavaScript frameworks, which is due to data immutability and ruling out side effects by usage of pure functions. But rather than comparing performance, Elm's main advantage is the fact that [the Elm architecture](https://github.com/evancz/elm-architecture-tutorial) suggests and encourages encapsulation of the view functionality into modular components, which makes them combinable and leads to the creation of reusable modules.

### Learning Elm

The Elm syntax might look odd at first – nevertheless it is very clear and does not take much time to get used to, in my experience.

```elm
module Main (..) where

import Html exposing (text, div, p, ul, li)
import Html.Attributes exposing (class)


feature description =
  li
    [ class "feature" ]
    [ text description ]


main =
  div
    [ class "welcome" ]
    [ p
        [ class "message" ]
        [ text "Elm is great, here's why …" ]
    , ul
        [ class "features" ]
        [ feature "It has a fast compiler with helpful error messages"
        , feature "Great performance due to immutability and pure functions"
        , feature "No more runtime exceptions!"
        ]
    ]
```

Elms standard library is relatively small compared to other languages, but rather than the syntax and core modules, it's the concepts which need to be learned and understood. Amongst others, these are the Elm architecture, immutability and purity, as well as [modelling problems the Elm way](http://elm-lang.org/guide/model-the-problem).

Elm is on the rise and it's already being used in production. It makes frontend developers around the globe happy and my bet is that we will hear more and more about Elm in 2016. So why not get started by diving into Elm yourself?

### Sounds interesting?

The following resources are a good starting point for diving into Elm, taking your own first steps and getting as excited as I am:

- [Elm: Building Reactive Web Apps](https://pragmaticstudio.com/elm) - a great introductory video course by the Pragmatic Studios. In about three hours you get to know about the core concepts and the Elm architecture by building a small app.
- [Let's be mainstream! User focused design in Elm](https://www.youtube.com/watch?v=oYk8CKH7OhE) - a talk by Evan Czaplicki, the creator of Elm, explaining the motivation behind developing a new functional programing language for the frontend. The talk also highlights the concepts, some features, and ideas as well as the reasoning for those.
- [Make the Back-End Team Jealous: Elm in Production](https://www.youtube.com/watch?v=FV0DXNB94NE) - talk by Richard Feldman about migrating a JavaScript/React app to Elm and the benefits thereof.
- [Elm - functional frontend development](https://dennisreimann.de/articles/elm.html) – my own series of articles about Elm in which you will learn about the language fundamentals as well as some advanced topics.
