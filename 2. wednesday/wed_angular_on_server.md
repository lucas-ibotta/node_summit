# Angular the Server
- by Stephan Fluian

## Why?
- for computers
  - SEO
  - Scrapers for previews from FB, Twitter, Reddit, etc
  - AMP - accelerated mobile pages
- for humans
  - shipping HTML from server
  - perceived load time benefits

## Angular Universal
- github.com/angular/universal
- github.com/angular/angular
  - various platforms
  - 4.0 release added platform server for server-side rendering
- `renderModuleFactory()`
  - pass in URL which goes to router
  - extra providers to override, change behavior
  - returns a promise of a string

## How is it possible?
- Angular is not DOM dependent, virtual or otherwise
- ? NativeScript project

## Node Setup
- @nguniversal/express-engine
  - middleware for express and server side Angular

## Remaining Hurdle of npm integration
- CommonJS (required) vs. UMD (what's used)
- Angular CLI to the rescue! `@angular/cli@next` 1.3.0
  - Multi-app support & server support
  - full steps process: bit.ly/universal-cli

## Preboot
- @angular/preboot

## The Future
- CLI 1.3 will support this, is RC right now
- Firebase, storage, hosting, bug tracking etc
  - cloud functions (just lambdas)
- `npm install ng-pwa-tools` ?
