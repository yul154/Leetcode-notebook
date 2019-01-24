# Topological Sorting
> A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices
* Detect DAG(directed acyclic graph)
* Dependency resolution

## Topological sort wit BFS(Kahn's Algorithms)
> Kahn's Algorithms (wiki)： BFS based， start from with vertices with 0 incoming edge，insert them into list S，at the same time we remove all their outgoing edges，after that find new vertices with 0 incoming edges and go on
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

```
def model_topological_sort(graph):
    indegrees=[0 for i in range(vertices_num)]# value is the number of connection it has
    outdegrees=[[] for in range(vertices_num)]# adjacent list
    queue=deque([index for index,node in enumerate(indegress) if not node])
    count=0
    while queue:
        cur=queue.popleft()
        count+=1
        for nei in graph[cur]:
            indegrees[nei]-=1
            if indegrees[nei]==1:
                queue.append(nei)

```
## Topological sort with DFS(Tarjan's Algorithms)
> Tarjan's Algorithms (wiki)： DFS based， loop through each node of the graph in an arbitrary order，initiating a depth-first search that terminates when it hits any node that has already been visited since the beginning of the topological sort or the node has no outgoing edges 
```
for each node:
    if not marked:
        if(dfs(node)==cycle): return cycle
return True

dfs(node):
    if node is visited: return ok
    if node is visiting: return cycle
    mark node is visiting
    for nei in graph[node]:
        if dfs(nei)==cycle: return cycle
    mark node as visited
    return ok
```


# 207 course schedule 

## Kahn's Algorithms
```
def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype
        """
        outdegrees=defaultdict(set) # outdegrees=[set() for i in range(numCourses)]
        for i in range(numCourses):
            outdegrees[i]=set()# some node is independent, so it's empty 
        indegrees=[0 for i in range(numCourses)]
        for courses,pre in prerequisites:
            outdegrees[pre].add(courses)
            indegrees[courses]+=1
        queue=deque([i for i in range(numCourses) if not indegrees[i]])
        count=0
        while queue:
            cur=queue.popleft()
            count+=1
            for nei in outdegrees[cur]:
                indegrees[nei]-=1
                if indegrees[nei]==0:
                    queue.append(nei)
        return count==numCourses
                    
```
## Tarjan's Algorithms
```
def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype
        """
        
        self.graph=[set() for i in range(numCourses)]
        for course,pre in prerequisites:
            self.graph[pre].add(course)
        def dfs(node):
            if self.visited[node]==-1: return False
            if self.visited[node]==1: return True
            self.visited[node]=-1
            for nei in self.graph[node]:
                if not dfs(nei): return False
            self.visited[node]=1
            return True
        for i in range(numCourses):
            self.visited=[0]*numCourses
            if not dfs(i): return False
        
        return True
```
```
def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype
        """
        self.graph=defaultdict(set)
        for i in range(numCourses):
            self.graph[i]=set()
        for course,pre in prerequisites:
            self.graph[pre].add(course)
        def dfs(node):
            self.visited[node]=-1
            for nei in self.graph[node]:
                if (nei not in self.visited and not dfs(nei)) or self.visited[nei]==-1 : return False
            self.visited[node]=1
            return True
        self.visited={}
        for i in range(numCourses):
            if (i not in self.visited and not dfs(i)) or self.visited[i]==-1 : return False
        return True
```
