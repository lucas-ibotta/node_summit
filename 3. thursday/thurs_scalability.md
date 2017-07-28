# Scaling the Unscalable
- David Clements / nearForm / @davidmarkclem
- Luca Maraschi / nearForm / @lucamaraschi

## Downtown Architecture
- Spotify Engineering Culture - doodle
- communication, more than 8 points of communication makes it feckin' hard
- Conway's law, organizations produce designs that are copies of their communication structure
  - big jumps in technology and communication much happen together

## ...from Monolith to MicroServices
- decompose monolith into units of work
- from silos to pods, from monolithic teams to spreading teams out
- detangling your teams

## Frontend Tho...
- decompose the backend and yet the front end is still a monolith!

## Demo
- docker-compose.yml
- four services in the compose file
- deploying a UI component as a service
- `riffi` - a js library to expose a module as a system?
- independently deployable modules on the front end
- a system built itself in real time

# WTF?
- expose modules as peers to the cloud
- published this 2 hours ago
- serializes components, so each module has its own dependencies
- SWIM protocol, consistent hash trees?
- Upring - application sharding for Node.js
- Distributed components, dependencies trees, module system, build system
- a run time for server-side rendering

## This is the next big thing
- "Abstract away logistical complexity"
