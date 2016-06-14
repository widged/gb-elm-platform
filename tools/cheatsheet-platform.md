**Elm 0.??**, **copied, please ignore** 

## Table of Contents
1. [Tools](#tools)
    * [REPL](#repl)
    * [Compile](#compile)
    * [Install Dependencies](#packaging)
2. [HTML Embedding](#html-embedding)


## Tools
#### REPL

`elm repl` / `elm-repl`

Import required modules
```elm
> import List
```

Get function signature
```elm
> List.map
<function> : (a -> b) -> List a -> List b
> (++)
<function> : appendable -> appendable -> appendable
```

Elm expressions return resulting value and type
```elm
> 1 + 1
2 : number
```

Backslash `\` is for multi-line expressions
```
> fn a b = \
|    a + b
<function> : number -> number -> number
```
 
#### Compile

`elm make` / `elm-make`

```bash
# Default compilation 
elm make HelloWorld.elm -> index.html

# Custom name
$ elm make HelloWorld.elm --output hw.js

# Multiple files
$ elm make HelloWorld.elm MyModule.elm --output hw.js

# With warnings
$ elm make HelloWorld.elm --warn

# To HTML
$ elm make HelloWorld.elm --output hw.html
```

#### Packaging

`elm package` / `elm-package`

Installation automatically adds `dependencies` in `package.json`.
```bash
# Install a package
$ elm-package install evancz/elm-html

# Specific version
$ elm-package install evancz/elm-html 1.0.0

# Diff two versions
$ elm-package diff evancz/virtual-dom  2.0.0 2.1.0
Comparing evancz/virtual-dom 2.0.0 to 2.1.0...
This is a MINOR change.

------ Changes to module VirtualDom - MINOR ------

    Added:
        attributeNS : String -> String -> String -> VirtualDom.Property
```

## HTML Embedding

Running fullscreen

`elm-make HelloWorld.elm` -> `elm.js`

```html
<script type="text/javascript" src="elm.js"></script>
<script type="text/javascript">
    Elm.fullscreen(Elm.HelloWorld);
</script>
```

Embed explicitly in a html element
```html
<script type="text/javascript" src="elm.js"></script>
<script type="text/javascript">
    var elmHolder = document.getElementById('hw-wrapper');
    
    Elm.embed(Elm.HelloWorld, elmHolder);
</script>
```

Run without graphics
```javascript
Elm.worker(Elm.HelloWorld);
```