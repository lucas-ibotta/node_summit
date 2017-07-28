# TypeScript - Trusting the Compiler
- Felix Rieseberg / Slack
- https://felix.fun

## JavaScript is EVERYWHERE!
- Slack moved app over to TypeScript from JS
- Nvidia drivers, Adobe Creative Suite, Atom, Slack are all JavaScript!
- more JavaScript, more worries
  - we must trust fellow developers
  - docs are always out of date
- often blows up at run time.

## TypeScript to the rescue!
- Superset of JS, so standard javascript will still work
- no modification at runtime
- excellent editor support, across all operating system
- npm integrations
- and, duh, TYPES

## Conversion
- rename the file from `.js` to `.ts`
- VSCode editor knows a lot right off the bat with normal javascript
- `tsc -init` - set tsconfig target
  - set es5 or es6 target
- `tsc` generates readable JS
- `npm install @types/request`

## Demo
- declare an interface Person
- strips out types when it's transpiled

## Porting Slack Desktop App
- turned on TS features and it found bugs right away
- start writing files in type script from now on
- you'll quickly dislike working with non-ported javascript files
- file by file, just add the types here rly quick
  - took a few months and it naturally ported over

## Benefits
- Committing with Confidence! structural dependencies are all sound
- ESlint, will enforce any dumb thing you want to enforce

## Downside
- JavaScript folks don't like Typed languages
- interfaces, type declarations, enums are hard for junior developers

## Q & A
- webstorm - can do it all without TypeScript ?
  - it's not bad, but developers are just insane
