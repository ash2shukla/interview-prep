# DFS

**Points to remember:**

The sequence to insert the neighbours matters.

**Algorithm:**

```python
adj_list = defaultdict(list)

visited = set()

def dfs(vertex):
    stack = [vertex]
    visited.add(vertex)

    while stack:
        vertex = stack.pop()
        for nbr in adj_list[vertex]:
            if nbr not in visited:
                visited.add(nbr)
                stack.append(nbr)

# this for loop is needed because there can be many components in graph.
for vertex in vertices:
    if vertex not in visited:
        dfs(vertex)
```
