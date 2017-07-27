# 0-60 with TypeScript
- Bowden Kelly from Microsoft

## Why TypeScript?
- focus on creating amazing things
  - instead, we're understanding, maintaining and writing code
  - only 33% of the time creating
  - as JS grows, less and less time spent writing
- Monaco, in browser - at 300K lines, 70% understand, 25% maintain, 5% create
  - VS Code evolved from Monaco

## Typescript
- superset of javascript, optionally typed
- tools to write better javascript, but it is just javascript
- add `//@ts-check` at start of file in VScode
- linting and validating existing javascript
- JsDoc types `@param` comment before function, checks types

## Does it work?
- academic research shows 15% of 400 bugs wouldn't have made it through TypeScript

## Express & TypeScript
- `tsc --init` generates a `.tsconfig.json` file, set compiler options
- `tsc` run typescript compiler
- can convert file from `.js` to `.ts` and add typescript, do it file by file

## Conversion to ES6
- `require("passport")` needs to be ES6 `import * as passport from "passport"`
- `module.export(User)` to `export default User`
- `import expressValidator = require("express-validator")`
- `index.d.ts` files - types from `@types` github account
  - ? automated types from popular repos to be checked
- auto-formatting

## VScode - I'm convinced
- terminal integrated
- documentation integrated
- @Microsoft/TypeScript-Node-Starter
- can add typescript to your existing workflow, works anywhere
