**Elm 0.17**, **shareable** 

## Diving in

### Starting with Elm without any installation

In the early stages of evaluation, you can compile and run simple Elm programs using [elm-lang.org/try](http://elm-lang.org/try), or ~~[share-elm](http://share-elm.com)~~ (if you want to save your code -- share-elm stuck at version 0.15). This is a good way to try out the example code given in tutorials.

For instance, if you paste this on [elm-try](http://elm-lang.org/try) and hit "Compile", it will print "Hello Elm!" on the screen.

```elm
import Html exposing (h1, text)

main =
  h1 [] [text "Hello Elm!"]
```

## Installing Elm

Once you start writing more complicated examples, you will need to install the *Elm Platform* on your machine. Visit [http://elm-lang.org/install](elm-lang.org/install) to get set up.

The *Elm Platform* provides a set of tools to execute code on the command line (`elm-repl`), run elm file in the browser (`elm-reactor`), install dependencies (`elm-package`), compile (`elm-compiler`), transpile to html (`elm-make`). They are each described in details in the [Tools section](tools/)

You will also need a text-editor. Common editors such as [Atom](https://atom.io/), [Sublime](http://www.sublimetext.com/), [LightTable](http://lighttable.com/) have lots of [Elm-specific plugins](http://elm-lang.org/install) to manage everything from syntax coloring to live reload.

It is also recommended (but not required) to [install elm-format](https://github.com/avh4/elm-format#installation-) and integrate it into your editor so that it runs on save.


## Get acquainted

Have a look at [the examples](http://elm-lang.org/Examples.elm).

See the [syntax reference](http://elm-lang.org/learn/Syntax.elm).
