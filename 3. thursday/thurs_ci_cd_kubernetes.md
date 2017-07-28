# Kubernetes CI/CD
- spinnaker.io
- @sandeepdinesh

## Spinnaker
- netflix product for CD for EC2 instances
- works at any scale
- Gitflow
  - develop, staging, master branch

## Workflow
- branch off, Travis tests on that branch
- pull request, merges back into master
- code ready to be deployed
- build a Google container (free tier)
- push to Google container registry, here comes Spinnaker
- `kubectl push` onto production! but should test first

## Spinnaker Flow
- Red/Black deployment
  - deploy completely fresh deploy, move load balancer over
  - wait 30 mins for monitoring
  - destroy old deployment after two hours, so we could switch back
- Rolling Red/Black
  - take them one at a time
- Another option to have monitoring in the middle of the rolling deploy
  - check 500s, other errors

## Google Cloud Stuff
- automatically tag Docker image with repo and commit SHA
- launch spinnaker into cloud launcher
- load balancers for staging and production
- create pipelines => "deploy to stage"
  - when docker images is updated, kubernetes deployment to staging
- add validation, based on another pipeline completing
  - requiring manual pipeline for confirmation
- then deploy to prod
  - get image from staging deployment itself, which is pretty cool.
  - it grabs that image and actually deploys it
  - we don't scale down the old instances, so we can rollback
  - add another manual validation before turning down previous deployment
  - resize previous group down to zero

## Rollback
- say no, turn on last deployment, turn off latest deploy
- more configurable pipelines, more granular
