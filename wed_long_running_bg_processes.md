# Long Running Background Processes
- Brandon Mayes / SPANNING Cloud Apps (SaaS Data Protection)
- @twofifty6
- bdmayes.github.io/nodesummit-longrunning

## Salesforce Backups
- runs in Node entirely
- backups, restores, cross-org restore, exports to CSV

## Async Responses
- Bluebird, Promises
- current options: respond in a callback or respond before a callback (bad idea)
- third thing!

## Worker Thread Patterns
- delegating responsibility to a queue, checking in on process
- long running function queue
- it returns a unique job id back the browser after creating it
- then periodically checks in on that job status from then on

## Tips for Robust Workers
- add retry logic, backoff
  - promise utils for while loops, adding in retries
- catch unhandled exceptions/rejections
  - keep job alive, log those errors
- resumability - leave breadcrumbs so it's resumable, not just restartable

## Challenges coming from Java
- designing synchronously
  - but there's not threads here!
- fast libraries development, use npm shrinkwrap
  - taking time on sprints to upgrade more often
- Order of operations still matters, even with async
  - Bluebird helps

## Monitoring
- internal logging tool, shows zombies
- slack alerts from Nagios w/ cloudwatch and InfluxDB
- if all else fails, throw them on a debug queue
  - route failed jobs to debug queue, with deeper level of logging
  - mdb for core dumps, debugging

## MBD
- virtualbox
- `npm install autopsy`
  - `autopsy setup` (more RAM is better)
  - `autopsy start`
  - `autopsy node core`
  - inspect variables, stack traces
  - ::jsfunction, ::jsobjects
- what happened?
  - requested bulk API request
  - should have returned a CSV
  - underlying library was synchronously saving CSV in memory

## Why Node instead of Java?
- Workload is i/o intensive, not CPU intensive
- non blocking i/o is a great fit for Node
- easy concurrency management without threads (concurreny: 10 in Bluebird)
- debugging without recompiling

## Lessons Learned
- delegate long-running tasks to workers
- message busses for interprocess communication
- fail gracefully
- carve out time for updating often
- monitor
- be paranoid, things will constantly fail, so be ready to handle it

## Struggled
- processes hang instead of fail. Possibly a hanging process?
  - generate a core dump `core-dump` library without killing it
- can't test things with production data as easily
