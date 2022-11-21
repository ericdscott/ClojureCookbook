# To Create a Clojure Project

The first step in developing a software is to create a project in your
dev environment.

There are several sets of tools available to accomplish this. The
creators of clojure have in recent years produce [a dedicated CLI
tool](https://clojure.org/guides/deps_and_cli) for this. Prior to
that, it was common to use [Leiningen], or [Boot] to create and manage
projects, and indeed may developers continue to do so.

There are also several different kinds of projects you may want to
create, some of which might be:
- An application with a command-line interface (CLI)
- A library, intended to inform other applications
- A web application

## Supports
- [Writing Software with Clojure]

## Done when:

- You have a minimal set of supporting code and configuration for your project.
- Said configuration informs your build tool enough that it can do its job.

### Some ways to confirm this
- You should be able to [launch a REPL] which [loads code] on your
  project classpath.
- You should be able to [run tests] (which may fail).

## Otherwise
- Navigate to your dev directory
- Continue per one of the options described below.

### To create a library project
#### With `neil` under the Clojure CLI
- [Configure your dev environment] per the
  [README](https://github.com/babashka/neil/blob/main/README.md) for
  neil
- enter `clojure -M:neil new lib MyLib` to establish a new project

### To create a CLI application project
#### With `neil` under the Clojure CLI
- [Configure your dev environment] per the
  [README](https://github.com/babashka/neil/blob/main/README.md) for neil
- enter `clojure -M:neil new app MyApp` to establish a new project

### To create a web application project
- Watch this space for discusson of [Luminus] and [kit-clj].

## Associated tools
- [Clojure CLI]
- [Leiningen]
- [Boot] 
- [deps-new](https://github.com/seancorfield/deps-new/)
- [neil](https://github.com/babashka/neil). 
- [Luminus]

---
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
