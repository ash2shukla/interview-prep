---
description: Greedy algorithm to find something based on some given intervals.
---

# Interval Scheduling

![](<../../../.gitbook/assets/image (1) (1).png>)

There are mainly two problems.

1. The intersecting parts ( ie. red part )
2. The union parts ( ie. green part )

Both Algorithms follow that (a, b) (b, c) are distinct.\
So Intersection condition is _**start < prev\_end**_

### Intersecting Intervals

_Shrink intervals when intersection found._

```python
intervals.sort(lambda interval: (interval.start, interval.end))
prev_end = float("-inf")
new_segments = 0
overlapping_segments = 0
for start, end in intervals:
    if start < prev_end:
        overlapping_segments += 1
        if end < prev_end:
            prev_end = end
    else:
        prev_end = end # because new segment has started we need to update end
        new_segments += 1
```

### Union Intervals

_Expand intervals when intersection found._

```python
intervals.sort(lambda interval: (interval.start, interval.end))
prev_start, prev_end = float("-inf")
new_segments = 0
overlapping_segments = 0      # additional interval to mark end of all intervals
for start, end in intervals + [(float("+inf"), float("+inf")]:
    if start < prev_end:
        overlapping_segments += 1
        if end > prev_end:
            prev_end = end # expand instead of shrinking
    else:
        prev_end = end # because new segment has started we need to update end
        new_segments += 1
```
