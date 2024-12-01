---
project: kneesocks
stars: 67
description: Put some nice SOCKS on your HTTP only program
url: https://github.com/bitinn/kneesocks
---

kneesocks
=========

_Put some nice SOCKS on your HTTP only program_

Motivation
==========

Driven by my burning desire to tunnel `npm install` requests through a SOCKSv5 proxy (eg. shadowsocks). Since `npm` only support HTTP proxy, I wrote this simple command line module to fire up a HTTP Proxy server, then use it to tunnel requests to my SOCKS proxy.

Features
========

-   Supports HTTP and HTTPS requests
-   Built-in DNS cache
-   150 loc, does nothing else

Install
=======

`npm install kneesocks --production -g`

Usage
=====

`kneesocks port1 port2`, eg. `kneesocks 10001 10002`

-   `port1` is the port your HTTP proxy server listen to on localhost.
-   `port2` is the port of your existing SOCKS proxy, also on localhost.

Then you can set your npm config:

-   `npm config set http http://127.0.0.1:10001`
-   `npm config set https-proxy http://127.0.0.1:10001`

To revert proxy config, use `npm config delete http` and `npm config delete https-proxy`.

To debug, use `DEBUG=proxy kneesocks port1 port2`

Limit
=====

-   Node v0.10+ required (Node v0.11+ preferred).
-   Probably not the best solution for day-to-day browsing, due to lack of remote dns and websocket support.
-   If you don't mind building binaries, use DeleGate or Polipo instead.

License
=======

MIT
