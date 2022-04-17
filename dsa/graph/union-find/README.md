# Union Find ( DSU )

A fast algorithm to find disjoint set unions in a graph.

**Path compression :** Set parent as u find other's parents.

```python
def find_parent(a):
    if parents.get(a, a) == a:
        return a
    else:
        # here path compression happens
        parents[a] = find_parent(parents.get(a, a))
        return parents[a]
```

**UF By Rank:** Always plug smaller tree under bigger. Rank just means depth of the tree

```python
def union(a, b):
    a_parent = find_parent(a)
    b_parent = find_parent(b)
    
    a_rank = ranks.get(a_parent, 0)
    b_rank = ranks.get(b_parent, 0)

    if a_rank > b_rank:
        parents[b_parent] = a_parent
    elif b_rank < a_rank:
        parents[a_parent] = b_parent
    else: # do whatever
        parents[a_parent] = b_parent
        ranks[b_parent] += 1
```
