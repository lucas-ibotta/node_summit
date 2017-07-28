# Shared Memory and Parallelism
- Jace A Mogill

## Super Computers & Node
- Cray 3 and AWS Data Center
- Data Center Scale in both cases
- Thread safe, read full, empty

## In Node // Parallel
- async, interweaves multiple requests into the event loop
- idea is the same as super computing data models
- fork-join parallelism - can fork and parallel, in and out and return
- bulk synchronous parallelism - wait for all threads to hit a barrier, sync up

## Cluster Outperforms Async
- github.com/syntheticsemantics/clustersync-vs-async-benchmark
- EMS.js (/ems repo)

## The Future
- nothing new is happening, it's all from the 80s
- server disaggregation
- process sharing
- non-volatile memory
- software defined memory
- shared persistent memory between Node and Python!?
