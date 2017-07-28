# Serverless Security
- Guy Podjarny / Snyk / @guypod
- bit.ly/faas-security-talk, theory of serverless security

## The Practice
- hacking a serverless function, aws lambda
- to-do list CRUD app with lambas
- many security concerns around servers are gone, but still application security concerns are here
- some libraries may be vulnerable
- ms library to parse "in three days"

## Catasrophic Backtracking
- regex parsing, denial of service attack with long running regex matching
- scale is abstracted away, so it's hard to exploit
- build time

## Other - ReDos
- dust.js vulnerability
- %27-console.log("NodeSummit was here") << url encoded and shows up in the logs
- require child process and curl back information about the environment
- remote command execution on the serverless, run `ls` and explore
- `/admin` folder, with `admin secrets` because not using the KMS

## Serverless Functions still have servers!
- don't rely on immutability
- servers are kept warm to run functions, not immutable
- could modify the binary and next run of function would be new code

## Perimeters
- No API Gateway to some of these lambdas
- can be invoked as part of an internal network, with hardcoded secret
- can call that function directionally

## Takeaways
- Do we use the key management system? KMS
- operationally free to run, but there may be cost to being hacked, worry about functions

```
curl -X POST https://jwqxr3xm49.execute-api.us-east-1.amazonaws.com/dev/todos --data '{ "text": "secure your application, dude!" }'
```
