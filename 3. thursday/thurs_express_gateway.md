# Express Gateway
- Al Tsang / LunchBadger / @altsang
- Shubhra Kar / Joyent / @ShubhraKar

## Microservices
- an ideal that's been out there for a long time
- best practice from decades of experience
- cloud-native technology makes it achievable
- an architectural style, not a blueprint

## API
- uniform API should be agnostic of under the hood implementation
- how to break apart legacy code into microservices? some patterns:
  - go along lines of business capabilities
  - divide along domains and subdomains
  - REST paradigm of a model (CRUD 'em)
- What units of granularity are best?
  - how many services per host?
  - what services per host?

## API Gateway
- the heart of microservices, one we don't want to build
- must play nicely with Kubernetes, conductor of services
- Problem 1: disparate microservices
  - clients talking to many other services, internal / external (stripe)
  - API Gateway must be centralized middleware to handle:
    - authentication
    - security
    - traffic control
    - ops
    - logging
- Problem 2: granularity concerns
  - client doesn't want to touch many tables directly
  - orchestrate many models, many tables
  - optimize end points, collapse requests

## Express Gateway
- you need superglue for these services, node is perfect for it
- everyone knows Express, already proven
- WHAT: dynamic express outfitted with middleware for API Gateway usecase
- WHEN: Launch is TODAY! whoah dude.

## Features & Benefits
- massive, dynamic, cloud native wrapper for express
- 80/20 with security and features for MVP
- policy wrapper - request comes in, eval params based on policy, hit service end point
- configured with YAML, many pipelines for many cases

## Real Life Use Case
- Challenge was to build something for:
  - exabyte scale, 200 Million + users
  - many auth schemes
  - rate limiting
  - offline sync
  - push notifications
- need container-native micro api gateway
- open source, framework agnostic, scalable

## Work Flow
- incoming web app, mobile app, desktop app
- goes to express gateway for auth (2fa, oAuth, JWT)
- gateway handles routing, throttling, metering
- backend as a system - access containers or other backends

## Conclusion
- installing is dead simple - `$ npm install -g express gateway`
- express-gateway.io
- LunchBadger is express, docker, kubernetes, portable solution
