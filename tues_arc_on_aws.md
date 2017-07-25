# WTF.JS - Node.js Cloud Functions Edition
- @brianleroux
- begin.com, a slack bot
- brianrioux.github.io/arc-preo
- arc.codes

# Provision, Deploy Lambdas
- servers > VMs > containers > cloud functions (lambdas)
- first three are a metaphor for a server
- that is going to go away

# Infrastructure as code
- repeatable everywhere
- three solutions:
  - terraform
    - own language HCL to deploy lambdas
  - serverless
    - yaml config
  - AWS SAM
    - took yaml idea
- problems
  - deep proprietary knowledge
  - manifest files in yaml, json are not ideal
  - metaphor is not a server anymore

# Architecture as Text > Infra as Code
- .arc files
1. comments with hashtag #
2. @ sections - @json, @events (sns), and more including dyanmo
3. the rest is text

- npm scripts - `npm run create` - runs locally
- `npm run deploy` - ships to staging
- `ARC_DEPLOY=production npm run deploy` to production

# Query params
- /foo/:bar is named params in URL
- $(params.bar) in HTML

# Q & A
- Skyliner - blog post on rollbacks
- there's no such thing, we always roll forward
- so this lets things move forward faster
