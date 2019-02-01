# cljs-perf
ClojureScript compilation time for a [specific `:sha`](https://github.com/mfikes/coal-mine/commit/1e8b057c2fa4aa8d07c1142e7be245331fdbfd9b) of the [Coal Mine](https://github.com/mfikes/coal-mine) corpus (newest at top):


|Version |Regular Build|Parallel Build| Java |
|--------|---------------:|-------------:|--------|
|[1,10.516](https://github.com/clojure/clojurescript/commit/8a5abc4e02c72d000204674f38c6665c786302a4) | 1814 s | 402 s | 1.8.0_192 |
|[1.10.439](https://github.com/clojure/clojurescript/commit/1e8b057c2fa4aa8d07c1142e7be245331fdbfd9b) | 1731 s | 380 s | 1.8.0_192 |
|[1.10.339](https://github.com/clojure/clojurescript/commit/b1ade48e21f9e7f78d9db74559ce4dd5846d0c94)|   3974 s | 812 s |1.8.0_162 |
|[1.10.329](https://github.com/clojure/clojurescript/commit/359d34ef57a436c05658a114f9f685c85e28d766)|  3852 s | 759 s|1.8.0_162 |
|[1.10.312](https://github.com/clojure/clojurescript/commit/6512df8321b16a819ea4cc870edf25b7c809947e) | 4119 s | 754 s |1.8.0_162 |
|[1.10.238](https://github.com/clojure/clojurescript/commit/98e2dbb89da75a4439f50d94d6a1c8f8ac62ba13)| 4027 s| 748 s|1.8.0_162 |

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

Dual hexa-core Mid-2012 Mac Pro, 128 GB
