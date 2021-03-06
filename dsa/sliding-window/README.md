# Sliding Window

{% embed url="https://leetcode.com/tag/sliding-window" %}

### Types of Questions

1. Find size of window given a constraint.
2. Find max min given size of window.
3. window + deque
4. window + dictionary / set&#x20;

### Fixed Size

```python
current_window = []

for end, element in enumerate(array):
    # if current_window size exceeded remove last element
    if end >= SIZE:
        current_window.remove(array[start])
        start += 1
    
    current_window.add(array[start])
    
    if is_valid(current_window):
        # correct result here
```

### Need to find size

```python
current_window = []

for end, element in enumerate(array):
    # add element to array
    current_window.append(element)
    while not is_valid(current_window):
        # try making window a valid window
        current_window.shrink()
        start += 1
    # window should be valid here
    valid_window = current_window
```
