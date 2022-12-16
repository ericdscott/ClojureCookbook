# To Manage Source Files

Writing code naturally requires creation of source files. In clojure
these files are associated with namespaces, which typically map to the
names of corresponding Java classes, addressable on the Java
classpath. This means that your project needs to be configured to
specify certain directories as containing a set of canonically named
file names in canonically named directories that reflect their
associated namespaces.

## Supports

- [Developing your code]

## Done when:
- Your source file compiles with a minimal namespace declaration.

### Some ways to determine this

- You should be able to evaluate the file with just the namespace
  declaration from your REPL without an error.

## Otherwise
- [Declare a source path in your project specification](#to-specify-a-source-path)
- Decide on a logical path for your namespace like `my-project.core`
- Create an [appropriately named file in an appropriate place in your
  source path](#to-locate-your-source-file)
- [Declare your namespace] at the top of the file using `(ns my-project.core)`

## To specify a source path

This is a list of directory entry points along which the compiler will
search for any namespaces it sees referenced in your code.

- options:
  - In a CLI `deps.edn` file
    - Use the `:paths` key for project-wide paths 
      - eg: `{:paths ["src" "resources"  ...]...}`
    - Use the `:extra-paths` key to bring in resources to inform specific aliases.
      - eg: `{:aliases {:test {:extra-paths ["test" ...]...}...}...}`
    
  - In a Leiningen `project.clj` file
    - use the `:source-paths` key 
      - at top-level for project-wide paths on your core logic
        - eg: `(defproject :source-paths ["src" "resources" ...] ...)"
      - within specific profiles as needed
        - eg: `(defproject :profiles {:dev {:source-paths ["dev"...], ...}...}...)`
    - use the `:test-paths` key for your testing modules
      - eg: `(defproject :test-paths {:extra-paths ["test" ...]...}...)`
    
## To locate your source file

- Let's assume that the logical path of the namespace you want to create is `my-project.core`
- Assume further that your project declaration has specified `src` as one of your paths
- Options:
  - For straight clojure:
    - Define the file as `./src/my_project/core.clj`
  - For straight clojurescript:
    - Define the file as `./src/my_project/core.cljs`
  - For shared logic between clojure and clojurescript:
    - Define the file as `./src/my_project/core.cljc`
    - [Use reader conditionals] to break out special cases between the two platforms.
      - eg: `(def cljc-error #?(:clj Exception :cljs js/Error))`


[verified group names]:https://github.com/clojars/clojars-web/wiki/Verified-Group-Names
[Developing your code]:./ToDevelopYourCode.md
[Use reader conditionals]:https://clojure.org/guides/reader_conditionals
[Declare your namespace]:https://www.clojure.org/guides/learn/namespaces#_declaring_namespaces
