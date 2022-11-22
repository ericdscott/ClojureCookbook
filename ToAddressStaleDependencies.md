# To Address Stale Dependencies

## Done when
- All dependencies declared for your project are up-to-date, and your code still works.

### Some ways to confirm this

- The tools below when invoked should yield empty lists
- Your tests should still pass

## Otherwise
- Using Clojue CLI
    - [Configure your dev environment] for `com.github.liquidz/antq`
    - `clojure -M:outdated`
    - [Update your Dependencies] accordingly
- Using Leiningen
    - [Configure your dev environment] for [lein-ancient](https://github.com/xsc/lein-ancient)
    - Enter `lein ancient` at the command line
    - [Update your Dependencies] accordingly

[Configure your dev environment]:./ToConfigureYourDevEnvironment.md
[Update your Dependencies]:./ToManageDependencies.md
[tests should still pass]:./ToRunTests.md
