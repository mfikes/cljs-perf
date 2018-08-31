# cljs-perf
ClojureScript compiler perf measurements. Raw time compiling Coal Mine source, and speedup relative to 1.10.238 in parenthesis.


|Release |Single-Threaded|Multithreaded|
|--------|---------------|-------------|
|1.10.238| 4027791.764564 msecs (1.00)| 748656.324444 msecs (1.00)|
|1.10.329|               | 759029.334984 msecs (0.98)|
|1.10.339|               | 818639.654404 msecs (0.91)|
|[`d2e4424cec693b59af67051aebefca971a477567`](https://github.com/clojure/clojurescript/commit/d2e4424cec693b59af67051aebefca971a477567) |               | 613959.738136 msecs (1.22)|
|[`c3732db435b37b5ebd5f87af3860007b39db697b`](https://github.com/clojure/clojurescript/commit/c3732db435b37b5ebd5f87af3860007b39db697b) |                | |

# Test Commands

Note: If you'd like to run a shorter test (perhaps to benchmark a candidate change), just compile `coal-mine/test-runner-1`.

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
