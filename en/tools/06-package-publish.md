**Elm 0.??**, **copied, please ignore** 

#### Documentation

Publishing a package requires well documented code.

```elm
module Documentation
    ( Type
    , value
    , anyfinCanHappen
    )
    where

{-| Module level documentation

# Just a header, what to include below
@docs Type, value

# About Anyfin
@docs anyfinCanHappen

-}

import Random exposing (int)

{-| Type level documentation comment -}
type Type = Bool

{-|-}
-- Empty comment above
value : Int
value = 1 + 1

{-| More on anyfinCanHappen -}
anyfinCanHappen : Generator Int
anyfinCanHappen =
    int 0 64

{-| This value is not exported, so isn't required -}
-- Use basic comment syntax
imNotExported =
    "Don't need to comment me"
```

* Documentation comment starts `{-|` ends with `-}`
* Module documentation comes after module declaration, before the imports
* Functions are grouped into related sections by keyword `@docs <args>` and declared with Markdown
* Each exported entity should have documentation comment on top of its declaration

(source: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/02-starting-out.md))

#### Publish

Add `README.md` otherwise publishing will fail<br/>
All packages start with initial version `1.0.0`<br/>
Versions all have exactly three parts: `MAJOR.MINOR.PATCH`<br/>
* `PATCH` - the API is the same, no risk of breaking code
* `MINOR` - values have been added, existing values are unchanged
* `MAJOR` - existing values have been changed or removed

`elm-package.json`
* `source-directories` - array of directories to look up for project source code inside the working directory
* `exposed-modules` - modules that exposed to a user after publishing, kind of interface to your internal API.

```bash
# elm-package.json
source-directories": [
    ".",
    "SubOne",
    "SubTwo"
]
"exposed-modules": [
    "SubOne",
    "Goodmodule",
    "Module"
]

├── SubOne
│   └── SubOne.elm        # Compiled and exposed
├── SubOne
│   └── SubTwo.elm        # Compiled, but unexposed
├── SubOne
│   └── SubThree.elm      # Compiler won't see the source, unexposed to the users
├── README.md
├── elm-package.json
├── Goodmodule.elm        # Compiled and exposed  
└── Module.elm            # Compiled and exposed
```

Publish
```bash
$ git tag -a 1.0.0 -m "initial release"
$ git push --tags

$ elm-package publish
```

Updating
```bash
$ elm-package bump

$ git tag -a 1.0.1 -m "secondary release"
$ git push --tags

$ elm-package publish
```

(source: [learnyouanelm](https://github.com/learnyouanelm/learnyouanelm.github.io/blob/master/pages/02-starting-out.md))

#### Publish

Elm's package manager enforces [semantic versioning](http://semver.org/), discouraging breaking changes. Packages therefore must tightly control what is exported. They want to hide their type definitions and helper functions, in order to present a stable, understandable, and helpful interface. Additionally anything that is exported must be documented.


## Organizing Tests and Examples

When writing a package, it's often useful to write tests or examples that use it. But, you don't want these to be included with the package, and certainly not in the compiled code that uses your package. Elm's tooling does not (currently) have an equivalent of Node's dev-dependencies or Ruby on Rails' development environment. So here is a trick to keep tests and their libraries separate from your package, while still being able to run the tests without publishing.

Create a new folder, say `test`, and copy `elm-package.json` there. Edit it and make these changes:
  * Change the version to `0.0.1`. This isn't strictly necessary but it helps prevent the tests from being released as their own package.
  * Under `"source-directories"`, change `"src"` to be `"../src"`. (If it's just `"."`, make it `".."`). Then add `"."` to the list.
  * Change the `"exposed-modules"` to be the empty list, `[]`. Tests are an application, after all.

Notice that we've kept all of the dependencies of the package in place. Now you can install any test toolkits you like into `test/elm-package.json` and they won't affect the main package. If the package's dependencies change, you will need to manually sync them to `test/elm-package.json`.

You can now write your tests or examples and import modules in your package as if it was installed in `elm-package.json`, but instead it's pulling from the parent folder with the original source. You just need to run `elm package` or `elm reactor` from inside the `test` folder.

(source: [elm-for-js](https://github.com/elm-guides/elm-for-js/blob/master/Modules,%20Exports,%20and%20Imports.md))