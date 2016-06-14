**Elm 0.17**, **shareable** 

# Package Manager

Elm relies on a package manager to install, share, and distribute libraries and manage dependencies in your projects. To get access to the package manager, you must install the `Elm Platform`.

On the command line, run `elm-package` or `elm package`. Without an argument, it will return help about options available. 

## elm-package.json

Like many package managers, the elm package managers stores all data about installed dependencies in a json file, `elm-package.json`. 

File: `elm-package.json`
```json
{
    "version": "1.0.0",
    "summary": "helpful summary of your project, less than 80 characters",
    "repository": "https://github.com/user/project.git",
    "license": "BSD3",
    "source-directories": [
        "."
    ],
    "exposed-modules": [],
    "dependencies": {
        "elm-lang/core": "4.0.0 <= v < 5.0.0",
        "elm-lang/html": "1.0.0 <= v < 2.0.0",
        "mgold/elm-date-format": "1.1.4 <= v < 2.0.0"
    },
    "elm-version": "0.17.0 <= v < 0.18.0"
}
```

If you only have one file, it's fine to keep it in the top level folder. Otherwise, you should create a `src` folder and keep all source files in there. You'll need edit `elm-package.json` to read `"source-directories": [ "src" ],` (don't forget the comma; `elm package` doesn't give a helpful error on invalid JSON).

In `elm-package.json`, A package will export at least one module in the `"exposed-modules"` field. 


## elm-stuff folder

All dependencies will be installed in a folder named `elm-stuff`. It is typically a good idea to add it to your `.gitignore` file when publishing elm code on github.  

## elm package install

The most common use of `elm package` is to install dependencies. In the root directory of your project, execute `elm-package install [PACKAGE] [VERSION]`. 

```bash
-- install the latest version compatible with other packages installed
$ elm package install elm-lang/mouse
-- install a specific version
$ elm-package install elm-lang/mouse 1.0.0
```

If a call to `elm package install` results in the installation of new files, the json file will be automatically updated. There is no need to add a '-i' parameter like you would with *npm*. 

All packages are installed in local mode. They are added to `elm-stuff/packages` folder, in your working directory. 

Extra parameters are available. Type `elm package install --h` for information on them. 

## elm-package diff

To rapidly check the changes that have been introduced between a version on you local machine and a new release, you can use `elm-package diff`. This will output all differences between the files. 

```bash
$ elm-package diff evancz/virtual-dom  2.0.0 2.1.0
Comparing evancz/virtual-dom 2.0.0 to 2.1.0...
This is a MINOR change.

------ Changes to module VirtualDom - MINOR ------

    Added:
        attributeNS : String -> String -> String -> VirtualDom.Property
```

## Searching for Packages

The full catalogue of community libraries is located at [package.elm-lang.org](http://package.elm-lang.org/).