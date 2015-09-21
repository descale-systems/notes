# What To Do With Logs

## People use:
- ELK
- RSyslog
- SyslogNG (helpful for tamper-proof logging using certificates)
- Sentry
- InfluxDB
- Graphite
- Logcheck
- Splunk
- Papertrail
- StatsD (and various reimplementations)
- FluentD
- Circuit breaking libraries

## What is the purpose of logging?
- Quite a lot of time spent reviewing, removing or at least filtering it.
- How best to filter logs that are generated to remove noise?
- Many use it for exceptions and security.

## Are text logs the best way to log data?
- Can metrics go straight to metric databases?
- Should they go to textlogs, and also to a specific log system?
- Crawling text logs is often painful
- There are few good ways to automate the filtration of logs
- It would be nice to have a system to filter out, but then gather verbose logs when an anomaly occurs

## Live error budgets
- For X requests, we are prepared to accept Y errors.
- If we go above Y errors in Z time, then we have an issue.

## When on-call, people should only be woken for issues that they can actually fix
- This is a technology issue and a people/process issue
- Having fall-back is great; having the process to trigger that is a problem
- Logs are things you look at after an incident; they shouldn't wake you up
- Being incredibly clear on what the priority on an incident is important
- Focus issues around the user to work the priority out
- Alert based on metrics, not just on text logs
- If you must alert on a text log, convert it to a metric first
- Define thresholds in relation to metrics
- It is useful to prioritise alerts and hosts on an importance basis
- Some people solely rely on external monitoring
- Should consider shipping projects with a healthcheck

- If you use a page telling users that you know about an issue, have a good process in place to make sure that you do actually work on an issue.

## How are logs synchronised?
- NTP is sufficient

## When starting out, there is often a cost associated with how you build infrastructure
- An ELK stack gets you some long way with logging:
- You get a dashboard
- You can query information
- Your logs go in, they get saved

## Facebook track 'karma' for each developer
- As a developer commits, release management team checks the commits
- The lower the karma, the more a diff gets reviewed before deployment
- It's a process for large corporations
- You may not need to be that big

## Log retention
- There are some regulatory requirements depending on issue
- Thirty days is common
- Anything over 30 days leads to possible potential for data protection requests
