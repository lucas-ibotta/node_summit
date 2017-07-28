# Debugging in 2017
- Paul Irish / Google / @paul_irish
- `console.log();`, there's more powerful ways to debug
- What is beyond `console.log`

## Tools
- `node --inspect hello.js` / `--inspect-brk` will break
- new tab in chrome `about:inspect`
- open "dedicated dev tools for Node"
- chrome stable has dedicated node window now! (as of this week)
- interactive and reruns/connects when making code changes

## Demo
- break points per line or within a line, arrow function
- step in (arrow button)
- right click, "blackbox script", ignores the Node callstack, ends up at own code
- control s, live edit with changes and rerun it without restarting node

## Other tools
- june07.com/nim
- @jaridmargolin/inspect-process

## Four Debugging APIs
1. start debugging existing node process?
  - it's not too late!
  - `process._debugProcess(pid)` in another terminal
2. `node inspect hello.js`
3. DevTools Protocol
  - connect to node's debugging port on client
4. `require('inspector')`
  - to use inside of node process

## Tracing
- `node --trace-events-enabled index.js`
- spits out a JSON file of the trace, which you can import into Chrome
- see v8 stats around timing of compiling, reading, parsing, network requests
- PR 14347
- `--trace-event-categories`
