# cljs-perf
ClojureScript compilation time for a [specific `:sha`](https://github.com/mfikes/coal-mine/commit/1e8b057c2fa4aa8d07c1142e7be245331fdbfd9b) of the [Coal Mine](https://github.com/mfikes/coal-mine) corpus (newest at top):


|Version |Regular Build|Parallel Build|
|--------|---------------:|-------------:|
|[`83866aa`](https://github.com/clojure/clojurescript/commit/83866aaf597f183877c0cf586c002f3b8b51d487) | 1764 s |
|[`4f37076`](https://github.com/clojure/clojurescript/commit/4f3707624846a2cf0345859e41370ec172da73c4) | 1997 s |
|[`980d1fa`](https://github.com/clojure/clojurescript/commit/980d1fa9f14a4ec5caad1e2a8b734795094e0eba) | 2190 s| 515 s|
|[`c3732db`](https://github.com/clojure/clojurescript/commit/c3732db435b37b5ebd5f87af3860007b39db697b) |  2570 s              | 579 s |
|[`b2a15b8`](https://github.com/clojure/clojurescript/commit/b2a15b86c46aaadb9b839015862629683db3f38e) | 2558 s|
|[`826b379`](https://github.com/clojure/clojurescript/commit/826b3790e91dff84f502e863d0c4f8cf15cc03a0) | 2539 s|
|[`f8b4125`](https://github.com/clojure/clojurescript/commit/f8b4125cbef671143b241881afdfc0195cf36480) | 2784 s |
|[`d38e001`](https://github.com/clojure/clojurescript/commit/d38e001b617c849be53fcc588b5a454e3acfa51d) | 3421 s|
|[`81a1ea1`](https://github.com/clojure/clojurescript/commit/81a1ea127974d43a6166fbdae33bcaa296fe9156) | 3848 s|
|[1.10.339](https://github.com/clojure/clojurescript/commit/b1ade48e21f9e7f78d9db74559ce4dd5846d0c94)|   3974 s | |
|[`d91207c`](https://github.com/clojure/clojurescript/commit/d91207cb7386365a07b563b09b6444846657a364) | 3800 s|
|[1.10.329](https://github.com/clojure/clojurescript/commit/359d34ef57a436c05658a114f9f685c85e28d766)|  3852 s | 759 s|
|[1.10.312](https://github.com/clojure/clojurescript/commit/6512df8321b16a819ea4cc870edf25b7c809947e) | 4119 s | 754 s |
|[1.10.238](https://github.com/clojure/clojurescript/commit/98e2dbb89da75a4439f50d94d6a1c8f8ac62ba13)| 4027 s| 748 s|

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
