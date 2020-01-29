# Reproducing a heap leak in linkerd2-proxy

A memory leak appears to be easily reproducible in recent proxy versions
under a variety of workloads. The leak(s) appear to correlate with HTTP
request load and TCP connection load.

This is easily reproducible with clients that initiate many connections.
Reproductions have been instrumented using both [HTTP/1.1][repro-http] and
[TCP][repro-tcp].

![HTTP test on master][rss-http-master]

![TCP test on master][rss-tcp-master]

![TCP test on branch][rss-http-branch]

![TCP test on branch][rss-tcp-branch]

[master]: https://github.com/linkerd/linkerd2-proxy/tree/release/v2.84.0
[repro-http]: ./burn-http.yml
[repro-tcp]: ./burn-tcp.yml
[rss-http-master]: ./rss-http-edge-20.1.4.png
[rss-tcp-master]: ./rss-tcp-edge-20.1.4.png
[rss-http-branch]: ./rss-http-d6bb2a82.png
[rss-tcp-branch]: ./rss-tcp-d6bb2a82.png
