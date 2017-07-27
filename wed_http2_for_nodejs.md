# HTTP2
- James Snell / @jasnell
- Open Source Architect for nearForm

## RFC 7540 (HTTP2)
- for Node Core
- `const http2 = require('http2')` is the product of one year and 45K lines of code
- opened PR last week for it last week, in review

## Thanks
- @tatsuhiro-t and the `nghttp` library
- taking over existing `http` npm module

## What works now? (code examples)
- push streams
- multiplexing, sending multiple requests at once
- flow control, sending data
- prioritization, deprioritize background tabs
- header compression, reduce 80% of traffic with headers having deltas of content requested
- plain text & TLS
- Client & Server
- Server-side Send File support

## What will work soon?
- upgrading from HTTP1
- client-side Send File

## Caveats
- all internals are different
- don't write to sockets directly
- compatibility with HTTP1 is not fully possible
- upgrade path, not for non-TLS HTTP1 examples

## When?
- in next v8 release in October
- Hopefully fully supported in 9.x
