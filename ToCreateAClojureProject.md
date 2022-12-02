# To Create a Clojure Project

## Contents
- [Supports](#supports)
- [Done when](#done-when)
- [Otherwise](#otherwise)
- [Associated tools](#associated-tools)

The first step in developing a software is to create a project in your
dev environment.

There are several sets of tools available to accomplish this. The
creators of clojure have in recent years produce [a dedicated CLI
tool](https://clojure.org/guides/deps_and_cli) for this. Prior to
that, it was common to use [Leiningen], or [Boot] to create and manage
projects, and indeed may developers continue to do so.

There are also several different kinds of projects you may want to
create, some of which might be:
- An Java application with a command-line interface (CLI)
- A library, intended to inform other applications
- A web application
- A shell script

Each of these kinds of projects will typically be initialized in different ways.

## Supports
- [Writing Software with Clojure]

## Done when...

- You have a minimal set of supporting code and configuration for your project.
- Said configuration informs your build tool enough that it can do its job.

### Some ways to confirm this
- You should be able to [launch a REPL] which [loads code] on your
  project classpath.
- You should be able to [run tests] (which may fail).

## Otherwise
- Navigate to your dev directory
- Continue per one of the options described below.
    - [To create a library project](#to-create-a-library-project)
        - [With `neil` under the Clojure CLI](#with-neil-under-the-clojure-cli-lib)
        - [With `Leiningen`](#with-lein-lib)
    - [To create a Java application project](#to-create-a-java-application-project)
        - [With `neil` under the Clojure CLI](#with-neil-under-the-clojure-cli-app)
        - ([Watch this space for leiningen](https://github.com/ericdscott/ClojureCookbook/issues/7))
    - [To create a web application project](#to-create-a-web-application-project)
    - [To create a shell script](#to-create-a-shell-script)       

### To create a library project

<a name=with-neil-under-the-clojure-cli-lib></a>
#### With `neil` under the Clojure CLI
  
- [Configure your dev environment] per the
  [README](https://github.com/babashka/neil/blob/main/README.md#clojure) for
  neil
- enter `clojure -M:neil new lib MyStuff/MyLib` to establish a new project

##### Follow-up

Your directory tree should look like this:

```
$ tree

.
├── build.clj
├── CHANGELOG.md
├── deps.edn
├── doc
│   └── intro.md
├── LICENSE
├── pom.xml
├── README.md
├── resources
├── src
│   └── MyStuff
│       └── MyLib.clj
└── test
    └── MyStuff
        └── MyLib_test.clj

6 directories, 9 files
```
<a name=with-lein-lib></a>
### With `Leiningen`

- [Configure your dev environment] to include [Leiningen]
- `$ lein new lib myStuff/myLib`


### To create a Java application project

<a name=with-neil-under-the-clojure-cli-app></a>
#### With `neil` under the Clojure CLI

- [Configure your dev environment] per the
  [README](https://github.com/babashka/neil/blob/main/README.md#clojure) for neil
- enter `clojure -M:neil new app MyStuff/MyApp` to establish a new project
- cd MyApp

##### Follow-up

Your directory structure should look like this:
```
$ tree

├── build.clj
├── CHANGELOG.md
├── deps.edn
├── doc
│   └── intro.md
├── LICENSE
├── pom.xml
├── README.md
├── resources
├── src
│   └── MyStuff
│       └── MyApp.clj
└── test
    └── MyStuff
        └── MyApp_test.clj
6 directories, 9 files
```

<a name=with-lein-app></a>
### With `Leiningen`

- [Configure your dev environment] to include [Leiningen]
- `$ lein new app myStuff/myApp`


### To create a web application project

- [Watch this space](https://github.com/ericdscott/ClojureCookbook/issues/8) for discusson of [Luminus] and [kit-clj].

### To create a shell script

- [Watch this space](https://github.com/ericdscott/ClojureCookbook/issues/9) for a discussion of [Babashka].


## Associated tools
- [Clojure CLI]
  - The official Clojure dependency manager
- [Leiningen]
  - An old reliable project manager that has lots of buy-in and associated tooling
- [Boot] 
  - A competitor to Leiningen. People say it gives you a lot more control over the details
- [deps-new](https://github.com/seancorfield/deps-new/)
  - A tool to be used under the Clojure CLI to build new projects
- [neil](https://github.com/babashka/neil)
  - A tool to be used under the Clojure CLI to do a bunch of things. Wraps `deps-new`.
- [Luminus]
  - A framework for developing web applications
  - Lots of plug-ins to do stuff like interact with databases
  - Kind of Leiningen-centric
- [kit-clj]
  - A newer framework being developed by the author of Luminus
  - Clojure CLI-centric
  
---
[Babashka]:https://babashka.org/
[Boot]:https://boot-clj.github.io/
[Clojure CLI]:https://clojure.org/guides/deps_and_cli
[Configure your dev environment]:./ToConfigureYourDevEnvironment.md
[Leiningen]:https://leiningen.org/
[Luminus]:https://luminusweb.com/
[Writing Software with Clojure]:./ToCreateSoftware.md
[kit-clj]:https://github.com/kit-clj/kit
[launch a REPL]:./ToLaunchARepl.md
[loads code]:./ToLoadCodeIntoARepl.md
[run tests]:./ToWriteAndExecuteTests.md
