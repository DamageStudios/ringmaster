## The Problem
Every day release engineers release code into production primarily based off a gut feeling. While many times this is accurate, often times it is not. When it's not accurate and production servers are down, this in turns causes engineering staffs to rollback the release or hurriedly try and patch the problem.

So how does the problem get solved?

## The Solution
Ringmaster is a tool for Release Management Risk Mitigation. It allows release engineers to take a deterministic approach to release management.

A deterministic system is a conceptual model of the philosophical doctrine of determinism applied to a system for understanding everything that has and will occur in the system, based on the physical outcomes of causality. In a deterministic system, every action, or cause, produces a reaction, or effect, and every reaction, in turn, becomes the cause of subsequent reactions. The totality of these cascading events can theoretically show exactly how the system will exist at any moment in time.

## How it works
Ringmaster shall determine how risky the changes are at a meta-level based initially on 4 factors and assign a score to each release:

* Size of diff
* Test plans quality and scope
* Discussion around the changes
* Developer Reputation System

### Size of diff
How big the diff is. The size of the diff. Bigger = more risky.

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
The quality of the test plan --> this can be based off code coverage %, unit tests P/F, integration tests P/F etc.

### Discussion around the changes
How much discussion there was around the PR. The amount of back-and-forth that occurred in the code review. The more back-and-forth, the more rejections, the more requests for change—the more risk.

### Developer Reputation System
Reputation System/Developer Karma --> ranking the Quality of a Developers Code --> Developers with a history of pushing garbage through get more scrutiny.




