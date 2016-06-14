**Elm 0.17**, **shareable** 

# Building and Deploying

Elm-reactor is great for the rapid development of elm projects. However, once it comes to deploying your files on a remote server, you will need access to html or javascript files.

The *Elm Platform* provides `elm-make` or `elm make` for compiling the elm code down to html or javascript. Type `elm make --h` for more information about what `make` does and what options are available.

If you pass a file to `elm make`, then you are writing an application. That file (and therefore module) is known as "Main". Create a `Main.elm` in your project directory. Compile with `elm-make Main.elm --output index.html`. The html file will contains a javascript tag with the compiled elm code as well as the logic required to embed any view declared in the elm code into the html document. 

If you require to integrate your elm component within a pre-existing html document, you can compile to javascript and manage the embedding logic yourself. Simply execute `elm-make Main.elm --output main.js`, then link to the resulting JavaScript in an HTML page. You can read about the specifics in the [html embed](app-framework/html embed) section of the app framework.

It's not necessary to call this file `Main.elm`, you can adopt any name you want. 

```bash
# Default compilation
elm make HelloWorld.elm 
// -- elm.js

# Custom name
$ elm make HelloWorld.elm --output hw.js

# Multiple files
$ elm make HelloWorld.elm MyModule.elm --output hw.js

# With warnings
$ elm make HelloWorld.elm --warn

# To HTML
$ elm make HelloWorld.elm --output hello.html
```

If you execute `elm make` with no additional arguments, then you create a Package. This compiles the modules listed, and subjects them to additional compile-time checks ensuring every exported value and type are documented properly. The compiler does not generate an HTML or JS output file.