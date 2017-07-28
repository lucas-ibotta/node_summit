## Quilt
- JavaScript to encode knowledge about how to run in the cloud
- A more simple version of Kubernetes, not compatible with Kubes though
- Kay Ousterhout
- kay@quilt.io

## Network Configuration
- specify ports
- where to run? set config

## Demo
- demo.quilt.io
- Node app with MongoDB
- `npm install -g @quilt/install`
- clone demo repo from Github
- `quilt daemon` - communicates with cloud, configured to AWS
- `quilt run` - deploy them, which is declarative
- `quilt show` - shows machines
- need more machines?
- edit `count` variable to equal new number. it accomplishes this total.
- `quilt run ./main.js` to deploy those changes
- can change cloud provider with one API. DigitalOcean, AWS, etc

## Why JavaScript for Ops?
- shareable, npm and github
- abstraction, importing modules, using variables (can't get that in YAML)

## Open Source
- git.quilt.io

## Q & A / Future
- private cloud?
- persistent storage between deploys
