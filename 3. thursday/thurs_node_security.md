# Security Panel
- Emily Rose / Salesforce / @nexxylove
- Bryan English / Intrinsic / @bengl
- Vladmir de Turckheim / Sqreen / @poledesfetes
- Gergely / Rising Stack / @nthgergo
- Guy Podjarny / Synk / @guypod

## Compromising Packages
- done transparently, whitehat hacker compromised half of all downloaded Packages
- reached out to npm, doing 2FA right is an obvious step forward

## Recommendations
- Committing packages with things linked to creds, like `.nsrc`
- use a password manager
- isolate accounts with publish writes, separate read only tokens
- security awareness and your posture around attack vectors
- start by caring
- risk assessment, know what you need to be watching for, what is at stake

## Is security is hard?
- professionals help
- being aware and doing little things like 2FA
- weakest link is the people (95% of hacks), so they need training
- "trust but verify"
- conflict between security culture and inclusive culture of node community?

## Red Team
- internal team to test everyone
  - phish own employees
  - badge phish other employees

## Serverless
- environment appears to be secure, privilege escalation
- doesn't change much on platform level of security
- hacking a serverless application talk later today
- Functions as a service, puts load onto service provider, a good idea
- convenience vs. security

## JavaScript
- is the language secure enough? types are an issue, type manipulation
- vulnerable packages, Buffer default behavior was leaking private memory
- every language has tendencies, which leads to security flaws
- express docs don't emphasize security implications of using default session keys
