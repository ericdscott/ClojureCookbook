# To Configure Your Dev Environment

Developing software amost always requires that you set certain
parameters to inform the development process.

Different tooling is typically available on different project
managers. Here we will concentrate (for now) on typical approaches
using the two most popular managers, the Clojure CLI, and Leiningen.

## Done when

You are satisfied with the ease with which you are developing your projects.

### Some ways to confirm this

This is largely subjective, but factors to consider are... (watch this space).

## Otherwise

- Under the Clojure CLI
  - [Install the Clojure CLI]
  - [Identify apppriate utiity] to enhance your programming experience
  - Documentation for this utility should tell you whether is is
    invoked with a `-M` `-X` `-A` or `-T` option
    - These options vary as to whether your local project's classpath
      is involved, how the entry point in the code is selected, and
      how arguments are passed
  - Options:
    - If the tool in question invoked with an `-X`, `-M` or `-A`
      argument (the docs should tell you):
      - [Define an alias] in your `~/clojure/deps.edn` for said utility.
        - Aliases declared in this file will be available everywhere on your computer.
    - If the utility in question is invoked with a `-T` option 
      - [Install the tool] with `clojure -Ttool install ...`

[Define an alias]:./ToDefineAnAliasInDepsEdn.md
[Identify apppriate tools]:./ToIdentifyDevelopmentTools.md
[Install the Clojure CLI]:./ToInstallTheClojureCli.md
[Install the tool]:./ToInstallClojureCLITool.md
