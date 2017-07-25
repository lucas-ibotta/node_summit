# Why Containers
- the best of a .zip file and a VM
- layered images, can share the lower level common parts of the instance
- can run two versions of Node on two images on one machine, and they're contained
- Docker takes out a layer of pre-provisioning (sizing out), is running directly on host kernel

### Container Advantages
- lower overhead
- faster. VMs take minutes. Docker takes milliseconds
- smaller. Node apps can be 60-70 MBs
- mirroring production and development environments
  - pull down an image and run it on local machine, debug
- scaling without worrying about the cloud provider
  - AWS is down? No worries. App can run generically on any vendor.

### Container Use Cases
- microservices & distributed architectures
- A/B Testing - almost identical versions, behind load balancer on one machine
- capturing services & infrastructure as code
  - docs around ports, endpoints, ENV variables

### Happy Ops
- immutability of containers, when running in production things can't change
- explicit dependencies, versioning
- fast boot & restarts
- scaling at the process level, can do rolling restarts for example

### Infrastructure as code
- Dialogue between Ops and Devs is simplifying, unifying
- pristine reference environments
- no "configuration drift", things like Chef, Puppet are built around locking in configuration
- Kube/Compose are like `package.json`

# Docker Overview
- uses LXC (linux containers) is a 30 year old technology, reintroduced
  - right time and right place
- layered filesystems for shipping images
- networking - docker images are linked to other containers, still considered private
- images are build with a `Dockerfile`

### Layering and Caching
- Docker commands create new layers
- Dockerhub image is layer one
- adding a feature adds another layer, describing change to the image
- top layer is the application
- `from: ` line. can optimize by building own image for developers
  - logging and monitoring tools can be baked in
- changes are git-style hashes, if not changes are made those layers are cached
- when adding new layers on top, only top is read-write
  - adding a layer sets lower levels to read-only
  - in practice, we end up with a flattened image where all layers come together
  - an `./etc` config would change from one layer to the next, but final image has right configuration

### Docker Hub
- hub.docker.com
- DockerHub :: Docker as Github :: Git

### $ docker pull
- `docker pull node:boron` (image:tag)
- seeing the layering system in action here, downloads only the different layers
- layers are shared at lower level, can be shared
- `docker run -it node:boron node -v` >> runs image and outputs the version
- `docker ps` - running processes, container id `8303ce2510c4`
- `docker exec -it 8303ce2510c4 node -v` >> same as above

### $ docker build
- each `KEYWORD` is a new layer, will cache each layer if not changed
- `docker build .`
- `docker build -f production/stuff/file_path`
- tagging with `-t`, example: `docker build -t nwhite/sample:v1`

```ruby
# Dockerfile

FROM node:boron

ENV NODE_ENV production
ENV PORT 5000
WORKDIR /app

EXPOSE $PORT

ADD package.json /app
RUN npm install --production

ADD ./app # copying a file, other option is COPY

ENTRYPOINT ["node", "app.js"]
```


### $ docker run / $ docker kill
- closing running docker image with `ctrl + c` doesn't work!?
  - `docker kill 8303ce2510c4`
  - run locally `docker run -p 5000:5000 nwhite/sample:v1` opens the port to 5000
- `docker run {image}`
- `docker run [OPTIONS] {image} {command}`
- `docker image -it` << interactive mode
- `docker image -d` << daemon mode, runs in the background

### docker tags
- `docker tag {source_image}:{tag} {target}:{tag}`
  - can overwrite the tags
  - be sure to always pull down latest image
  - use git-sha as the tag from release

### $ docker push
- `docker push {image}:{tag}` - publish docker images

### cleaning up
- `docker rmi - $(docker images -a)` - removes all images
- `docker rm -f $(docker ps -a)`
- `docker image prune` - built in commands
- `docker container prune`

### What goes in a container?
- your app, dependencies, nothing else!
- [dumb-init](https://github.com/Yelp/dumb-init), created by yelp
- in Dockerfile `ADD/RUN dumb-init`

### Best practices
- define user and group, limit permissions. Devops 101
- minimize layers, be aware of the layer caching
  - squash layers with multiple setup commands on one line
  - all as one `RUN`, private key example in one RUN command, is cached at `COPY`

```ruby
# dockerfile optimization

RUN apt-get update \
&& apt-get upgrade -y --force-yes \
```

# Architecture
- one load balancer, you're ok.
- nested services is when you need...

## Orchestration management
- restart machines
- provide a private network
- scale up and down, as long as things are stateless
- service discovery

## Kubernetes 101
- automatic binpacking
- horizontal scaling, "hey, if we hit 80% memory, add machines"
- automated rollouts and rollbacks
- storage orchestration, abstracted away
- self-healing, can configure back-off times
- device discovery, load balancing
- secret and configuration management

## Vocabulary (in nested order)
- nodes - worker machines, could be a VM
  - called minions in older versions
  - each Node has ability to run pods

- namespace - virtual clusters are called namespaces
- deployment
- replica set
- pod, containers - typically one to one
  - containers on one pod can act like being on one localhost
  - smallest deployable unit
- service - decoupling of pods. service discovery
  - policy for accessing a service
- replica sets - for scaleability
- labels & selectors
  - key value pair on objects like pods
  - lables identify attributes, must be unique
  - selectors identify a set of objects
  - empty selectors select every object

## Networking
- Docker model
  - host-private networking
  - docker images can only talk with machines on same machines
  - communicating across nodes requires allocation of ports, forwarding to proxied containers
- Kubernetes model
  - all containers can talk with each other
  - IP address is the same of for the machine itself & what other machines see
  - less complex overall. manages dynamic port allocation gracefully

## Kubectl
- "kube control"
- google cloud platform (GCP), azure have kubernetes UIs
- objects defined in .yaml files
- AWS kubernetes environemt? Where is the documentation?
- 3 deploys
  - console
  - nginx secure proxy
  - storage
- [nsolid](https://github.com/nodesource/nsolid-kubernetes) example
- kubectl autocomplete for zshrc

```bash
$ kubectl config view
$ kubectl config current-context
```

## finding and viewing resources
- `kubectl explain pods` - help docs
- `kubectl get services --all-namespaces` - or deployements, pods, etc

## updating resources
- made to be flexible, so devops can do whatever they want to do
- so many ways to do things, don't be overwhelmed. they're all right.
- so building higher level scripts to abstract use-cases away for developers
- `kubectl rolling-udate {version-to-find} {version-to-update}`
- `kubectl replace --foce -f ./pod.json`
- `kubectl expose rc nginx --port=80 --target-post=800`

## scaling
- `kubectl scale --replicas=3 -f foo.yaml`

## delete
- `kubectl delete -f ./pod.json`

## other stuff
- `kubectl logs my-pod`
- `kubectl run -i` - parity back to docker
- `kubectl attach my-pod -i`
- exec
- `kubectl cordon my-node` - unschedule that node
- `kubectl drain my-node` - clear stuff onto another machine
- `kubectl uncordon my-node`

## Putting images onto a cluster
- `kubectl create -f service.yaml` - make a service from a file
- `kubectl create -f deployment.yaml` - make a deployment
- [examples in nsolid](https://github.com/nodesource/nsolid-kubernetes/tree/master/conf)
- add more cluster size (?) so there's a load balancer in front of a service (?) (? wtf is the vocab?)

## Cloud Providers
- Microsoft azure has advantage
  - have a server managing your nodes and access to it
- Google cloud platform
  - doesn't allow access into the server node to customize
  - resizing and dynamic changes are under the hood
  - fine for 95% of cases, but could cause hiccups in production

Joe Doyle / Nathan White
@JoeDoyle23 / @_nw_
jdoyle@nodesource.com / nw@nodesource.com
