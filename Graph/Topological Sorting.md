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

## Iteration
```
def canFinish(self, numCourses, prerequisites):
        degrees=[0]*numCourses
        new_cour={}
        count=0
        for cou,pre in prerequisites:
            degrees[cou]+=1
            if pre not in new_cour:
                new_cour[pre]=[]
            new_cour[pre].append(cou)
        stack=[i for i in range(len(degrees)) if degrees[i]==0]
        while stack:
            cur=stack.pop()
            count+=1
            if cur in new_cour:
                for nei in new_cour[cur]:
                    degrees[nei]-=1
                    if degrees[nei]==0:
                        stack.append(nei)
        return count==numCourses
                    
```
## DFS recursive
```
def canFinish(self, numCourses, prerequisites):
        def dfs(graph,node,visited):
            visited[node]=0
            for nei in graph[node]:
                if (nei not in visited and not dfs(graph,nei,visited)) or visited[nei]==0:
                    return False
            visited[node]=1
            return True
        graph=[[] for i in range(numCourses)]
        visited={}
        for u,v in prerequisites:
            graph[u].append(v)
        for v in range(numCourses):
            if v not in visited and not dfs(graph,v,visited):
                return False
        return True
```
