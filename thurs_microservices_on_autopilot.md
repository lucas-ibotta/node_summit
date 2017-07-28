# MicroServices on Autopilot
- Wyatt Preul / Joyent
- slides: jsgeek.com/nodesummit

## The Story of Chicken-Mirco
- service is decomposed from monolith
- independent deploy, disposable and quickly iterate

## Antipatterns:
- load balancer between MicroServices
  * if timeout, how do we know other services are healthy for retry?
- "startup order matters"
  * we don't need to assume an order for boot
  * connecting to MySQL db on boot for a service
- MicroServices AnitPatterns by Mark Richards, free Oreily book

## Autopilot Pattern
- Apps can work the same on laptop and in any data center
- not married to infrastructure
- [autopilotpattern.io]
- github.com/autopilotpattern, examples of solutions with docker containers
- container pilot - free open source tool
- container health check will query services and report to `consul`
- Example

## Self Healing
- services stop sending requests to unhealthy services
- take down the serializer service
- check healthy address for DB service.
  - IF none, use in-memory storage
  - IF yes, send the data there
- ContainerPilot for service registration
  - telemetry reporting with prometheus, any metric you care about
  - github.com/@joyent/containerpilot ? - written in go

## Demo
- Hapi Circut Breaker
- Consul discovers Nats instances
- you can choose pattern of connecting, round robin, random

## Load Balancers
- purpose at the edge, not between services
- don't expose them directly to your customers
