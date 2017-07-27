# Twitter Lite on Node.js
- @jbell / James Bellinger
- two years of development, launched 3 months ago
- complete rewrite of Twitter webstack. First Node app.

## The year is 2015
- old webapp is JS front end, married to a Scala backend
  - form validation, fetching pages
- slow to compile, hard to maintain
  - had to write front end, then go write backend support in Scala
  - lots of waiting for Scala to compile

## Twitter Lite
- technology was almost there
- optimized for slow internet speeds
- ludicrously developable
- remove server from the load path

## Teach Up
- Educate / Evangelize about the tech within the company
- @kpk / @ryanoneill / @necolas did the work
- dependency differences
  - Scala relies upon 100 external libraries- vetted by security team
  - Node service has 2000 dev dependencies
    - service layer runs in sandbox, accesses public Twitter API like any other
- confidence of integration tests
  - sentry.io - browser based open-source error catching

## Teach the Team (soft part of switching)
- learn and teach all the tools
- watch Wednesdays - lunch as a team, watch a video with lunch, talk about 'em
- weekly blame-free retrospectives - fail faster
- record everything in a spreadsheet
  - see patterns, like redux anxiety
  - what did we learn?
  - what are we not talking about
  - what matters that went well?
  - risk of blackholes of large projects - spreadsheet showed evidence of incremental progress

## Node in Prod (hard part of switching)
- Scala & thrift vs. Node v8 & json
  - experiment config was 400KB, which is hard to parse
- flamegraphs from Netflix team, great for debugging node apps
  - flat parts show where CPU is overloaded. should be spikey.
- best option is to parse less. had to change it to 40KB, 50% compute times
- Node clients are more sensitive to API limits. Everyone wins.
- GraphQL is up next

## Results
- compute cost is 6% of the JVM version
- there's a browser element of that, but it's 3.5% on 1 billion requests
- Engineering efficiency: 30 min deploy (scala) vs. 6 min on Node
- Compiling times: 4 mins (scala) to 1 second (almost instant)
