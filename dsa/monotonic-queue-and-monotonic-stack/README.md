# Monotonic Queue and Monotonic Stack

{% embed url="https://leetcode.com/tag/monotonic-stack" %}

{% embed url="https://leetcode.com/tag/monotonic-queue" %}

A queue that has only one tone ( ie. goes only in one direction if all elements were plotted )

There are primarily two types of mono queues\
1\. Mono max queue\
2\. Mono min queue

![](<../../.gitbook/assets/image (2).png>)

### Mono max queue

We have an array and want to keep track of elements that are greater than current element.

```python
while queue and queue[-1] < num:
    queue.pop()
else:
    queue.append(num)
```

It works because if an element is smaller than current element it wouldn't matter for computing maxs after this index.

### Mono min queue

We have an array and want to keep track of elements that are smaller than current element.

```python
while queue and queue[-1] > num:
    queue.pop()
else:
    queue.append(num)
```

It works because if an element is greater than current element it wouldn't matter for computing mins after this index.
