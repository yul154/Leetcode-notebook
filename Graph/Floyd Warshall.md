# Floyd Warshall
> Find the lengths of the shortest paths between all pairs of vertices of the given directed graph

## Application
* no negative circle
* finding the lengths (summed weights) of shortest paths between all pairs of vertices
* finding the transitive closure of a relation or widest paths between all pairs of vertices in a weighted graph.

## Core of algorithm:
1. Store the weight of edges in a two-dimensional array, if there is no connection between two vetices, the weight is infinite
2. dynamic formula: d(k)ij = min(d(k-1)ij, d(k-1)ik+ d(k-1)kj) (1<= k <= n)
>For every pair (i, j) of source and destination vertices respectively, there are two possible cases.
>1) k is not an intermediate vertex in shortest path from i to j. We keep the value of dist[i][j] as it is.
>2) k is an intermediate vertex in shortest path from i to j. We update the value of dist[i][j] as dist[i][k] + dist[k][j].
3. Time complexity: O(n^3)
4. Space complecity: O(n^2)

```
Input:
       graph[][] = { {0,   5,  INF, 10},
                    {INF,  0,  3,  INF},
                    {INF, INF, 0,   1},
                    {INF, INF, INF, 0} }
which represents the following graph
             10
       (0)------->(3)
        |         /|\
      5 |          |
        |          | 1
       \|/         |
       (1)------->(2)
            3       
Note that the value of graph[i][j] is 0 if i is equal to j 
And graph[i][j] is INF (infinite) if there is no edge from vertex i to j.

Output:
Shortest distance matrix
      0      5      8      9
    INF      0      3      4
    INF    INF      0      1
    INF    INF    INF      0 

```

## Implementation
```
graph = defaultdict(lambda: defaultdict(int))
for u,v,w in edges:
    graph[u][v]=w
    for k in range(len(edges)): 
        # pick all vertices as source one by one 
        for i in range(len(edges)): 
  
            # Pick all vertices as destination for the 
            # above picked source 
            for j in range(len(edges)): 
                graph[i][j] = min(dist[i][j] , 
                                  dist[i][k]+ dist[k][j] 
```


## 399
```
def calcEquation(self, equations, values, queries):
        graph=defaultdict(lambda:defaultdict(int))
        for (u,v),w in zip(equations,values):
            graph[u][v]=w
            graph[v][u]=1.0/w
        
        for k in graph:
            graph[k][k]=1.0
            for i in graph:
                for j in graph:
                    if graph[i][k] and graph[k][j]:
                        graph[i][j]=graph[i][k]*graph[k][j]
        res=[]
        print(graph)
        for i,j in queries:
            res.append(graph[i][j] if graph[i][j] else -1.0)
        return res


```
