# To Configure Your Dev Environment

Developing software amost always requires that you bring in tooling
and set certain parameters to inform the development process.

Different tooling is typically available on different project
managers. Here we will concentrate (for now) on typical approaches
using the two most popular managers, the Clojure CLI, and Leiningen.

There are also full-featured editors and IDEs. Traditionally using
[Cider under Emacs](#emacs-cider) has been popular among Clojurians,
but VI(#vi) also has tooling. Under VS Code the Calva(#calva) project
is gaining popularity. Under IntelliJ, Cursive(#cursive) is the usual
plugin.

## Done when

You are satisfied with the ease with which you are developing your projects.


### Some ways to confirm this

This is largely subjective, but typically you should find it easy to 
- manage dependencies
- fire up a REPL
- jump around in your code by clicking on stuff
- lint your code
- create, install and deploy an uberjar or related artifact

## Otherwise

- Under the Clojure CLI
  - [Install the Clojure CLI]
  - [Identify apppropriate utiities] to enhance your programming experience
  - Documentation for this utility should tell you whether is is
    invoked with a `-M` `-X` `-A` or `-T` option
    - These options vary according to whether your local project's classpath
      is involved, how the entry point in the code is selected, and
      how arguments are passed
  - Options:
    - If the tool in question invoked with an `-X`, `-M` or `-A`
      argument:
      - [Define an alias] in your `~/clojure/deps.edn` for said utility.
        - Aliases declared in this file will be available everywhere on your computer
    - If the utility in question is invoked with a `-T` option 
      - Inspect the set of installed tools with `clojure -Ttools list`
      - [Install the tool] with `clojure -Ttool install ...`

- Under Leiningen
  - [Install Leiningen](#to-install-leiningen)
  - [Identify plugins](#finding-leiningen-plugins) to enhance your programming experience
  - [Add said plugins](#adding-lein-plugins)

## Leiningen

### To install Leiningen

https://leiningen.org/ is the homepage. It is well-documented. See the
`Install` section.

### Leiningen Plugins
#### Finding Leiningen plugins

Consult [the Leiningen plugins listing].

#### Adding Leiningen plugins

Plugins can either be added to your individual project of to your
`~/.lein/profiles.clj` file using this pattern...

```clj
{:user {:plugins [[lein-ancient "0.6.15"] ...]}}
                  
```
## Emacs/Cider

https://github.com/clojure-emacs/cider


## Vim

https://www.deepbluelambda.org/programming/clojure/programming-clojure-with-vim

## Calva

https://calva.io/

## Cursive

https://cursive-ide.com/

[Define an alias]:./ToDefineAnAliasInDepsEdn.md
[Identify apppropriate utiities]:./ToIdentifyDevelopmentTools.md
[Install the Clojure CLI]:./ToInstallTheClojureCli.md
[Install the tool]:./ToInstallClojureCLITool.md
[the Leiningen plugins listing]:https://codeberg.org/leiningen/leiningen/wiki/Plugins
