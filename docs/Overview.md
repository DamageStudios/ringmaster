## The Problem
Every day release engineers release code into production primarily based off a gut feeling. While many times this is accurate, often times it is not. When it's not accurate and production servers are down, this in turns causes engineering staffs to rollback the release or hurriedly try and patch the problem.

So how does the problem get solved?

## The Solution
Ringmaster is a tool for Release Management Risk Mitigation. It allows release engineers to take a deterministic approach to release management.

A deterministic system is a conceptual model of the philosophical doctrine of determinism applied to a system for understanding everything that has and will occur in the system, based on the physical outcomes of causality. In a deterministic system, every action, or cause, produces a reaction, or effect, and every reaction, in turn, becomes the cause of subsequent reactions. The totality of these cascading events can theoretically show exactly how the system will exist at any moment in time.

## How it works
Ringmaster shall determine how risky the changes are at a meta-level based initially on 4 metrics and assign a score to each release:

* Size of diff
* Test plans quality and scope
* Discussion around the changes
* Developer Reputation System

Each of the above 4 metrics should be used to assign a overall score to the release with no single metric accounting for more than 35% of the overall score.

### Size of diff
How big the diff is. The larger the diff is in terms of the number of changed files and the number of additions/deletions the riskier the release should be scored. 

You can calculate the percent difference between a known value A and a calculated value B  using this formula:
```
         |A - B|
% dif = --------- * 100%
            A
```
In this example, A = 2645; B = 2689. so their difference, A - B is 44 and hence the percent difference is:
```
         |2645 - 2689|
% dif = --------------- * 100% = 1.664% increase
                 12
```
Less than 2% so the assumption that x was negligibly small is good.

### Test plans quality and scope
The quality of the test plan can be used as a metric in factoring in the viability of a release. 

This score can be calculated on the following events:

* Code Coverage percentages in terms of increase and decrease
* Number of unit test failures
* Number of integration test failures

### Discussion around the changes
How much discussion there was around the Release.  The more back-and-forth, the more rejections, the more requests for change—the greater the risk.

This score can be calculated on the following events:

* CommitCommentEvent (GitHub) 
* IssueCommentEvent (GitHub) 

### Developer Reputation System
The Developer Reputation System ranks the Quality of a Developers Code so that Developers with a history of pushing garbage through get more scrutiny at release time. 

Developers are rated on a starring system on a scale of 1-5 with 5 being the highest rating one can achieve. All Developers start from a baseline of 3 stars.

This score can be calculated based on the following GitHub activity stream events (This is just a sample):

* CommitCommentEvent 
* IssueCommentEvent 
* IssuesEvent 
* PullRequestEvent 
* PushEvent 
* CreateEvent 

Other events that can be calculated are:
* Number of good builds developer is responsible for
* Number of bad builds developer is responsible for
* Number of good past releases the developer is responsible for
* Number of past bad releases the developer is responsible for



