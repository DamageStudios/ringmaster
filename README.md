Ringmaster is a tool for Release Management Risk Mitigation. It allows release engineers to take a deterministic approach to release management.

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

This is in essence is a dashboard to provide information to the release engineering team as the viability of a release.