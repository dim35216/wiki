# Dijkstra algorithm

## Input
Directed, weighted graph G = (V, E) with non-negative edge weights w; start node s (single-source shortest-path SSSP)

## Pseudocode
```
For all nodes v in V:
    v.dist = INF; v.pred = NULL
s.dist = 0
H = BuildHeap(H) // MinHeap or FibHeap
While(H is not empty):
    u = H.ExtractMin()
    For all nodes v in AdjList[u]:
        if v.dist > u.dist + w(u, v): // Relax
            v.dist = u.dist + w(u, v); v.pred = u
            H.DecreaseKey(v, v.dist)
```

## Shortest path algorithms
|                	|         	|                SSSP                	|                    APSP                    	|  Thin graph  	|
|---------------:	|--------:	|:----------------------------------:	|:------------------------------------------:	|:------------:	|
|       Dijkstra 	|   Array 	|         O(\|V\|^2 + \|E\|)         	|          O(\|V\|^3 + \|V\| \|E\|)          	|    O(n^3)    	|
|       Dijkstra 	| MinHeap 	| O(\|V\| log\|V\| + \|E\| log\|V\|) 	| O(\|V\|^2 log\|V\| + \|V\| \|E\| log\|V\|) 	| O(n^2 log n) 	|
|       Dijkstra 	| FibHeap 	|      O(\|V\| log\|V\| + \|E\|)     	|      O(\|V\|^2 log\|V\| + \|V\| \|E\|)     	| O(n^2 log n) 	|
|  Bellmann-Ford 	|         	|           O(\|V\| \|E\|)           	|              O(\|V\|^2 \|E\|)              	|    O(n^3)    	|
| Floyd-Warshall 	|         	|                  -                 	|                 O(\|V\|^3)                 	|    O(n^3)    	|
|        Johnson 	|         	|                  -                 	|     O(\|V\|^2 log \|V\| + \|V\| \|E\|)     	| O(n^2 log n) 	|

SSSP: single-source shortest-paths (1:n)  
APSP: all-pairs shortest-paths (n:m)  
For Dijsktra: non-negative edge weights only  
For FibHeap: [Amortised analysis](https://hpi.de/friedrich/teaching/units/amortisierte-analyse.html) gives the worst-case time complexity for sequences of operations
