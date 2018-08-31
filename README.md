# cljs-perf
ClojureScript compiler perf measurements. Raw time compiling Coal Mine corpus.


|Version |Non-Parallel Build|Parallel Build|
|--------|---------------:|-------------:|
|[1.10.238](https://github.com/clojure/clojurescript/commit/98e2dbb89da75a4439f50d94d6a1c8f8ac62ba13)| 4027 s| 748 s|
|[1.10.312](https://github.com/clojure/clojurescript/commit/6512df8321b16a819ea4cc870edf25b7c809947e) | |
|[1.10.329](https://github.com/clojure/clojurescript/commit/359d34ef57a436c05658a114f9f685c85e28d766)|               | 759 s|
|[1.10.339](https://github.com/clojure/clojurescript/commit/b1ade48e21f9e7f78d9db74559ce4dd5846d0c94)|               | 818 s|
|[`d2e4424`](https://github.com/clojure/clojurescript/commit/d2e4424cec693b59af67051aebefca971a477567) |               | 613 s|
|[`c3732db`](https://github.com/clojure/clojurescript/commit/c3732db435b37b5ebd5f87af3860007b39db697b) |  2570 s              | 579 s |

# Test Commands

To run a shorter test, instead compile `coal-mine/test-runner-1`.

## Single Threaded

```
 clj -J-Xmx16g -Srepro -Sdeps '{:deps {org.clojure/clojurescript {:git/url "https://github.com/clojure/clojurescript" :sha "98e2dbb89da75a4439f50d94d6a1c8f8ac62ba13"} github-mfikes/coal-mine {:git/url "https://github.com/mfikes/coal-mine" :sha "1e8b057c2fa4aa8d07c1142e7be245331fdbfd9b"}}}' -m cljs.main -co '{:parallel-build false :compiler-stats true}' -d `mktemp -d` -c coal-mine/test-runner
```

## MultiThreaded

```
 clj -J-Xmx64g -Srepro -Sdeps '{:deps {org.clojure/clojurescript {:git/url "https://github.com/clojure/clojurescript" :sha "98e2dbb89da75a4439f50d94d6a1c8f8ac62ba13"} github-mfikes/coal-mine {:git/url "https://github.com/mfikes/coal-mine" :sha "1e8b057c2fa4aa8d07c1142e7be245331fdbfd9b"}}}' -m cljs.main -co '{:parallel-build true :compiler-stats true}' -d `mktemp -d` -c coal-mine/test-runner
```

# Java

```
java -version
java version "1.8.0_162"
Java(TM) SE Runtime Environment (build 1.8.0_162-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.162-b12, mixed mode)
```

# Hardware

Dual Hexacore Mid-2012 Mac Pro, 128 GB
