**Elm 0.17**, **shareable** 

Elm is a language for creating web pages and web applications using Functional Programming techniques. Its syntax is somewhat like Haskell, but more friendly, and aimed at front-end web development. Elm compiles into JavaScript, so Elm programs are normally run in a browser, and provide ways to create and interact with html content.

Elm was made by Evan Czaplicki, who continues to develop it with the support of [NoRedInk](https://www.noredink.com/). It is currently used in production by several companies, including [CircuitHub](https://www.circuithub.com/) and [NoRedInk](http://tech.noredink.com/). (source: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/01-introduction.md))

## Elm in a nutshell

Elm is made of three parts. The Elm language, the Elm Platform, and the Elm Application framework.

### Elm Language

The Elm language is a *functional programming language*, where functions are *stateless*. Functions have no side-effects. The only thing a function can do is calculate something and return it as a result. If a function is called twice with the same parameters, it's guaranteed to return the same result. This is a property that makes testing, debugging and refactoring code very easy. It also makes it easy to build more complex functions by gluing simple functions together. (adapted from: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/01-introduction.md))

The Elm language is *statically typed*. When you compile your program, the compiler knows which piece of code is a number, which is a string and so on. That means that a lot of possible errors are caught at compile time. Elm uses a very good type system that has *type inference*. That means that you don't have to explicitly label every piece of code with a type because the type system can intelligently figure out a lot about it. If you say a = 5 + 4, you don't have to tell Elm that a is a number, it can figure that out by itself. Type inference also allows your code to be more general. If a function you make takes two parameters and adds them together and you don't explicitly state their type, the function will work on any two parameters that act like numbers. (adapted from: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/01-introduction.md))

Even if you don't explicitly specify the type, the compiler detects errors and provide readable compiler messages. The program cannot be compiled until all errors have been fixed. No runtime exceptions! No possible ambiguity about values of null or undefined. This gives incomparable reliability.

The strict typing leaves no room for ambiguity about values of null or undefined.

The Elm language is *elegant and concise*. Because it uses a lot of high level concepts, Elm programs are usually shorter than their imperative equivalents. And shorter programs are easier to maintain than longer ones and have less bugs. (source: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/01-introduction.md))

### Elm Platform

The *Elm Platform* provides a set of tools. Tools to execute code on the command line (`elm-repl`), run elm file in the browser (`elm-reactor`), install dependencies (`elm-package`), compile (`elm-compiler`), transpile to html (`elm-make`). A quick overview of the *Elm Platform* is given here and the various tools are detailed in the [Platform section](platform/).

### Elm Application Framework

* Unidirectional Application Architecture (similar concepts as Redux)
* Immutable data structures
* Module system and core libraries
* Built-in tooling and Package manager
* HTML, CSS, JavaScript interoperability
* Outperforms most popular rendering libraries

(source: merged, [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/02-starting-out.md))