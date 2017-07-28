# Routing Tiny Payments with Ingerledger.js
- Stefan Thomas / @justmoon
- works at Ripple
- @interledger / interledger.org / gitter

## Payments systems are outdated
- companies have hidden the complexity of the system
- Stripe, Venmo, etc aren't **changing** the system
- What can we do though?
  - Blockchains! Bitcoin came out!
  - But that hasn't turned out, transaction fees are super high
- as volume increases, cost goes down (and vis-a-versa)
- payments should have super low transaction cost

## "internetworking"
- "internet"
- first about the size of the network
- now, as they're connected, it all became about the speed
- reach turns into speed as it grows
- apply that to payments
- Visa advertising their own reach
- Bitcoin scaling is a pain in the ass

## Interledger Project
- example: file upload service
- module `koa-ilp`
- server side `ilp.pad({ price: 10 })` - require payment for using this endpoint
- client side `superagent-ilp`
- interledger connectors = connects payment networks

# Big Picture
- Internet economy is incomplete
- All protocols suffer from barter problem
  - Torrents splits a file into smaller pieces, so you can share pieces instantly
- Bartering require coincidence
- Marketplaces centralizing content, taking a cut
- "When a service is free, you're the product" - Tim Cook
- Advertising is annoying, users are opting out
  - the napster moment, users opting out
- Money solves the barter problem. Direct exchange of money.

## Examples
- webtorrent-ilp @emscschwartz on github
  - pay for media AS you stream it
- TUMO - pay for curated playlists, github.com/haykadamyan/playlist-store
- Flat rate payments - allows more engagement, since folks don't want to pay
- ilp-kit - open payments in the browser
  - Wc3 standard
  - merchant and browser
  - merchant and interledger wallet
