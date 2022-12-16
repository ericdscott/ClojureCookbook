# To Manage Dependencies

Clojure projects invariably build on resources published under Maven
and in git repositories. Tools like the Clojure CLI and Leiningen use
configuration files to declare where these dependencies are located,
and what versions are being referenced.

## Supports
- [Creating software in Clojure]

## Done when

- Your project brings in dependencies for all the functionality support you need

### Some ways to confirm this
- [View your dependency tree from the command line](#to-view-your-dependency-tree)
- [Confirm that your dependencies are up-to-date]

## Otherwise
- Find resources that will provide the functionality you need
  - ([watch this space](https://github.com/ericdscott/ClojureCookbook/issues/22))
- Options:
  - Under Clojure CLI 
    -[ Edit the `:deps`
    section](https://clojure.org/guides/deps_and_cli#_running_a_repl_and_using_libraries)
    of your `deps.edn`
    - Extend dependencies to specific aliases with `:extra-deps` keys
  - Under Leiningen
    - [Edit the `:dependencies`
      section](https://codeberg.org/leiningen/leiningen/src/branch/stable/doc/TUTORIAL.md#user-content-dependencies)
      of your `project.clj`

## To view your dependency tree

- Options:
  - under Clojure CLI:
    - `clojure -X:deps tree`
  - under Leiningen:
    - `lein deps tree`

[Confirm that your dependencies are up-to-date]:./ToAddressStaleDependencies.md
[Creating software in Clojure]:./ToCreateSoftware.md

    
