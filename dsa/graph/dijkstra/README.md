# Dijkstra

Implementation wise its just a BFS with min priority queue.

**Algorithm**

```python
adj_list = defaultdict(list) 
# adj_list contains vertex1 = [(vertex2, weight_of_vertex1_to_vertex2), ...]

pq = [(0, start_vertex)]

smallest_weights = {}

while pq:
    cost, vertex = heappop(pq)

    if vertex not in smallest_weights:
        smallest_weights[vertex] = cost

        for nbr, nbr_cost in adj_list[vertex]:
            heappushh(pq, (cost+nbr_cost, nbr))


```
