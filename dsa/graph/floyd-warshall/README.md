# Floyd Warshall

**Time Complexity :** $$O(n^3)$$

**Space Complexity :** $$O(n^2)$$****

**Points to remember**

1.  can be used to find transitive closure as well.

    _if there's a path from_ $$i$$ _to_ $$j$$ _through_ $$k$$ _then_ $$adj[i][j] = true$$

**Algorithm**

```python
adj_matrix = [[]] # adjacency matrix V*V
path_matrix = deepcopy(adj_matrix) # resultant path matrix V*V

# here V = number of vertexes

for k in range(n):
 for i in range(n):
  for j in range(n):
     path_matrix[i][j] = min( path_matrix[i][j], 
                        path_matrix[i][k] + path_matrix[k][j])
     # for transitive closure
     # path_matrix[i][j] or (path_matrix[i][k] and path_matrix[k][j]) 
```
