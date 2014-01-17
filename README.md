Ringmaster is a tool for Release Management Risk Mitigation. It allows release engineers to take a deterministic approach to release management.

A deterministic system is a conceptual model of the philosophical doctrine of determinism applied to a system for understanding everything that has and will occur in the system, based on the physical outcomes of causality. In a deterministic system, every action, or cause, produces a reaction, or effect, and every reaction, in turn, becomes the cause of subsequent reactions. The totality of these cascading events can theoretically show exactly how the system will exist at any moment in time.

Determine how risky the changes are at a meta-level:

* How big the diff is. The size of the diff. Bigger = more risky.
* The quality of the test plan.
* How much discussion there was around the PR. The amount of back-and-forth that occurred in the code review. The more back-and-forth, the more rejections, the more requests for change—the more risk.
* Reputation System/Developer Karma --> ranking the Quality of a Developers Code --> Developers with a history of pushing garbage through get more scrutiny.

Need to hook into:

* Jira
* GitHub
* Code Climate?
* Travis-CI/Jenkins/Bamboo fail/pass stats

This is in essence is a dashboard to provide information to the release engineering team as to the viability of a release.