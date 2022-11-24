# To Convert Leiningen Projects to Clojure CLI deps.edn projects

If you have a project working under Leiningen, but feel that the trend
is shifting toward the Clojure CLI, you may want to refactor your
project accordingly.

[This post by Sean Corfield] discusses why his team transitioned to the Clojure CLI.

https://clojureverse.org/t/is-there-a-sales-pitch-for-switching-to-deps-edn-from-lein-in-2020/5367

## Supports
- [Maintaining your project]

## Done when
A previously working project using a leiningen project.clj file now works under the clojure CLI.

### Some ways to confirm this

- Assuming you could do `lein uberjar` before, you should be able to run `clojure -T:build ci` and generate an equivalent result.
- `clojure -T:build test` should work the same as `lein test`
- if applicable, `clojure -M:cljs-test should work for clojurescript testing

## Otherwise
- [Install the Clojure CLI] as needed
- Options:
  - Follow the [directions from practical.li]
  - [Use depify](#to-use-depify) and clean up the output
- Copy the source for [build.clj](#build.clj) below into a local
  `build.clj`
- Adapt the `lib` and `version` variables in `build.clj` to your project
- Add the [`:build` alias] below into your `deps.edn`
- If clojurescript is a dependency
  - Add the [`:cljs-test` alias] below into your `deps.edn`
  
  
### To Use depfiy

- [Configure your dev environment] to use the [depify-alias](#depify-alias) below
- In your project directory enter `$ clojure -M:depify > deps.edn`

#### depify-alias

```
{ :aliases :depify
           {:extra-deps {hagmonk/depify {:git/url "https://github.com/hagmonk/depify"
                                         :sha "b3f61517c860518c1990133aa6eb54caf1e4d591"
                                         }}
            :main-opts ["-m" "depify.project"]
            }
}
```

### `:build` alias

Put this in your project `deps.edn` to reference `build.clj`

```clojure
{:aliases
           ;; Building utilities
           ;; invoke with -T:build
           ;; for help: clojure -A:deps -T:build help/doc
           :build {
                   :deps {
                          io.github.seancorfield/build-clj {:git/tag "v0.8.2"
                                                            :git/sha "0ffdb4c"}
                          }
                   :ns-default build
                   }
}                   
```

### build.clj

This is source for a build tool to put in your project at toplevel.


``` clojure
(ns build
  "Adpated from https://github.com/seancorfield/deps-new/blob/develop/resources/org/corfield/new/lib/root/build.clj"
  (:refer-clojure :exclude [test])
  (:require [clojure.tools.build.api :as b] ; for b/git-count-revs
            [org.corfield.build :as bb]))

(def lib 'my-stuff/my-thing)

(def version "0.1.0-SNAPSHOT")

(defn test "Run the tests." [opts]
  (bb/run-tests opts))

(defn ci "Run the CI pipeline of tests (and build the JAR)." [opts]
  (-> opts
      (assoc :lib lib :version version)
      (bb/run-tests)
      (bb/clean)
      (bb/jar)))

(defn clean "Cleans any clj/s compilation output.
  Where:
  `opts` := `m` s.t. (keys m) may match #{:include-caches?, ...}
  `include-caches?` when truthy indicates to clear .cpcache and .shadow-cljs directories.
  "
  [opts]
  (println (str "Cleaning with opts:" opts "."))
  ;; TODO: check opts
  (bb/clean opts)
  (b/delete {:path "./out"})  
  (b/delete {:path "./cljs-test-runner-out"})
  (when (:include-caches? opts)
    (println (str "Clearing caches"))
    (b/delete {:path "./.cpcache"})  
    (b/delete {:path "./.shadow-cljs"}))
  opts)

(defn install "Install the JAR locally." [opts]
  (-> opts
      (assoc :lib lib :version version)
      (bb/install)))

(defn deploy
  "Deploy the JAR to Clojars. Using $CLOJARS_USERNAME and $CLOJARS_PASSWORD"
  [opts]
  (-> opts
      (assoc :lib lib :version version)
      (bb/deploy)))


```
### `:cljs-test` alias

Add this alias to your `deps.edn` to support clojurescript tests

```clojure
{:aliases
           ;; Test cljs version with `clojure -M:test-cljs`
           ;; Get help with clojure -M:test-cljs --help
           ;; See also https://github.com/Olical/cljs-test-runner
           :cljs-test {
                       :extra-deps {olical/cljs-test-runner {:mvn/version "3.8.0"}}
                       :extra-paths ["test"]
                       :main-opts ["-m" "cljs-test-runner.main"]
                       }
}
```

## Other tools
- [lein-tools-deps]
  - Lets you reference deps in your `project.clj`
- [lein-to-deps]


[Configure your dev environment]:ToConfigureYourDevEnvironment.md
[Install the Clojure CLI]:./ToInstallTheClojureCli.md
[Maintaining your project]:./ToMaintainYourProject.md
[This post by Sean Corfield]:https://corfield.org/blog/2021/02/23/deps-edn-monorepo/
[`:build` alias]:#build-alias
[`:cljs-test` alias]:#cljs-test-alias
[directions from practical.li]:https://practical.li/clojure/alternative-tools/clojure-cli/migrating-to-clojure-cli-tools.html
[lein-to-deps]:https://github.com/EwenG/lein-to-deps
[lein-tools-deps]: https://github.com/RickMoynihan/lein-tools-deps

