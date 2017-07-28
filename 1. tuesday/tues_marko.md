# Marko <3 Node.js
- @psteeleidem twitter
- marko, lasso, morphdom

## Ebay
- built Marko for Ebay's massive scale
- switched to Node.js in 2013
- Marko is a UI library

## Streams
- you can stream HTML to the browser
- progressive HTML rendering, flushing it down incrementally in chunks
- only helpful if you're doing async rendering
- not many are doing this right
- Express does *not* support streaming

## Use cases
- 1 billion pages @ ebay
- mobile ebay website (library is >10k gzipped)

## Why Marko & Node.js
```bash
$ npm install marko
$ npx marko-cli create my-app
```
- modules - any module can be a marko module
- async - `<await(person from Person)> </await>` for promises
- readability - has a jade/pug concise syntax
- single file UI components - updating DOM, with diffs like React
- scoped `components/` - shared and within each route
- FAST - better IO/s than React
