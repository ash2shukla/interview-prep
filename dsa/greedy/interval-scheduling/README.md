---
description: Greedy algorithm to find something based on some given intervals.
---

# Interval Scheduling

![](<../../../.gitbook/assets/image (1).png>)

There are mainly two problems.

1. The intersecting parts ( ie. red part )
2. The union parts ( ie. green part )

For intersection after sort a new part is starting when the next start exceeds previous min end.

![](<../../../.gitbook/assets/image (17).png>)

_in above example if we focused on the maximum end then we would only see 1 intersection whereas there are two._

For union after sort a new part is starting when next start exceeds previous max end.
