**Elm 0.17**, **shareable** 

# Local REPL

The `Elm Platform` gives access to a REPL, on the command line. A REPL is a Read-Eval-Print Loop that let you experiment with simple expressions or check the functionality of imported libraries. 

To start the REPL, type `elm repl` or `elm-repl` at the command line. 

It is useful to explore the resulting value and type of simple expressions. 

```elm
> 5 + 1
6 : number
> List.map
<function> : (a -> b) -> List a -> List b
> (++)
<function> : appendable -> appendable -> appendable
```

Any non core dependency must be imported first. 

```elm
> import Dict -- Import required modules
> Dict.get
<function> : comparable -> Dict.Dict comparable a -> Maybe.Maybe a
```

## Things to know. 

Type `:exit` to exit.

You can spread your code over multiple lines with a backslash `\` at the end of the line.  Be sure not to have any whitespace after the backslash. A `|` will be added at the start of the line, to acknowledge that the next line is treated as a continuation of the current line.

```elm
> fn a b = \
|    a + b
<function> : number -> number -> number
```




