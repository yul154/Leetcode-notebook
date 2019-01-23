# Topological Sorting
> A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices
* Detect DAG(directed acyclic graph)

```
def topsort(graph):
    def topsort(graph):
    degrees=dict((u,0) for u in graph)
    for u in graph:
        for v in graph[u]:
            degrees[v]+=1
    print(degrees)
    start=[u for u in degrees if degrees[u]==0]
    res=[]
    print(start)
    while start:
        cur=start.pop()
        res.append(cur)
        for v in graph[cur]:
            degrees[v]-=1
            if degrees[v]==0:
                start.append(v)
    return res
```

# 207 course schedule 

```

```
