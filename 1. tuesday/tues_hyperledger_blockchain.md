# Blockchains for Business
- for business ideas, identity over anonymity
- selective endorsement over proof of work
- tracking assets over cryptocurrency
- private chains, no need for consensus or proof of work
- Hyper Ledger not being used in production anywhere

## Requirements for Business Blockchains
- shared ledger
- smart contracts
- privacy
- trust - only commit trusted changes

## Benefits
- saving time
- removing costs
- reduce risk
- increase trust - regulators can see everything

# Hyperledger
- linux foundation project
- dec 2015, open source projects, 7 or so
- fabric, composer
- many members
- open source
- weekly calls
- hyperledger.org
- hyperledget.github.io
- Docker images

### HyperLedger Composer
- framework to build on top of platform (Fabric)
- business centric API and laungauge
- easily integrate blockchain solutions with existing processes
- released in March 2017

### Open development tools
- DSL for data modeling
- javascript business logic
- web playground to test
- client library in npm
- editor support
- CLI utilities
- code generation with yeoman
- integration with Loopback & swagger

# Demo (Lifecycle of a vehicle)
- building a car (as the manufacturer would)
  - "purchase and build" - record transaction into ledger
  - status updates throughout the production of the car
- car buyers
- regulators
  - can see order, through delivery

### Model File
```
asset Vehicle identified by vin (
  integer vin,
  string color,
  ...etc
  )
```

### Swagger
- Swagger Condegen - generate SDK for your API

### Yeoman Generator
- `yo hyperledger-composer:angular`
  - makes an Angular4 App, with each asset CRUD features

### Node RED
- integrates existing systems with blockchain
