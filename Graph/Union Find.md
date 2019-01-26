# Union Find

* Dynamic connectivity of a list of node
  * DC: afte union a new node ,detech groups
* Using in undirect grpah

## algorthim:
  1. build n groups
  2. traversal nodes and figure out which group they belong to(find)
  3. if they are not in a same group, union(union)
  4. if in a sam group, pass
```
tags=[i for i in range(n)]

def find(e,tags):
    if tags[e]==e:
      return True
    else:
      find(tags[e],tags)# find an ancestor

def union(e1,e2):
    root1=find(e1,tags)
    root2=find(e2,tags)
    if root1==root2:
      return 
    else:
      tag[root2]=root1
```
## 200
```
def find(e,tags):
            if e==tags[e]:return e
            else: return find(tags[e],tags)
def union(n,a,b,c,d,tags):
    index1=a*n+b
    index2=c*n+d
    root1=find(index1,tags)
    root2=find(index2,tags)
    if root1!=root2:
        tags[root2]=root1
    else:
        return 
def numIslands(grid):
        if not grid or not len(grid) or not len(grid[0]):
            return 0
        row,col=len(grid),len(grid[0])
        tags=[0 for i in range(row*col)]
        for i in range(row):
            for j in range(col):
                if grid[i][j]=='1':
                    tags[i*col+j]=i*col+j
                else:
                    tags[i*col+j]=-1
        
        for i in range(row):
            for j in range(col):  
                if grid[i][j]=='0':continue
                if j+1<col and grid[i][j+1]=='1':
                    union(col,i,j,i,j+1,tags)
                
                if i+1<row and grid[i+1][j]=='1':
                    union(col,i,j,i+1,j,tags)
        count=0
        for i in range(len(tags)):
            if tags[i]==i:
                count+=1
        print(tags)
        return count
```
## 261
```
def validTree(self, n, edges):
        
        def find(e,tags):
            if e==tags[e]:return e
            else: return find(tags[e],tags)
            
        if len(edges) != n - 1:  # Check number of edges.
            return False
        tags=[i for i in range(n)]
        for u,v in edges:
            root1 = find(u, tags)
            root2 = find(v, tags)
            if find(u,tags)!=find(v,tags): tags[root2]=root1
            else: return False
        return True
            
```
## 323

```
def countComponents(self, n, edges):
    """
    :type n: int
    :type edges: List[List[int]]
    :rtype: int
    """
    tags=[i for i in range(n)]# union find

    def find (e,tags):
        if e==tags[e]: return e
        else: return find(tags[e],tags)
    for e1,e2 in edges:
        root1=find(e1,tags)
        root2=find(e2,tags)
        if root1!=root2:
            tags[root1]=root2
            n-=1
    return n
```
## 399
 ```
 def calcEquation(self, equations, values, queries):
        tags,weights,res={},{},[]
        for (u,v),w in zip(equations,values):
            if u not in tags:
                tags[u]=u
                weights[u]=1.0
            if v not in tags:
                tags[v]=v
                weights[v]=1.0
            self.union(u,v,tags,weights,w)
        for e1,e2 in queries:
            if e1 not in tags or e2 not in tags:
                res.append(-1.0)
            else:
                root1,root2=self.find(e1,tags,weights),self.find(e2,tags,weights)
                if root1!=root2: res.append(-1.0)
                else: res.append(weights[e1]/weights[e2])#
        return res
 def union(self,e1,e2,tags,weights,w):
     root1=self.find(e1,tags,weights)
     root2=self.find(e2,tags,weights)
     if root1!=root2:
         tags[root1]=root2
         weights[root1]=w*(weights[e2]/weights[e1])#
 def find(self,e,tags,weights):
     if e!=tags[e]:
         p=tags[e]#
         tags[e]=self.find(tags[e],tags,weights)
         weights[e]=weights[e]*weights[p]#
     return tags[e]
 ```
## 547
```
def findCircleNum(self, M):
        """
        :type M: List[List[int]]
        :rtype: int
        """
        count=length=len(M)
        tags=[i for i in range(length)]
        for i in range(length):
            for j in range(length):
                if M[i][j]==1:
                    root1=self.find(i,tags)
                    root2=self.find(j,tags)
                    if root1!=root2: 
                        tags[root1]=root2
                        count-=1
        return count

def find(self,e,tags):
    if e!=tags[e]: return self.find(tags[e],tags)
    return tags[e]
```

```
def findCircleNum(self, M):
     n=len(M)
     tags=[i for i in range(n)]
     def find(e,tags):
         while e!=tags[e]:e=tags[e]
         return e
     for i in range(n):
         for j in range(i+1,n):
             if M[i][j]:
                 tags[find(i,tags)]=find(j,tags)

     return sum(i==tags[i] for i in range(n))
        
```
## 684
```
def findRedundantConnection(self, edges):
        """
        :type edges: List[List[int]]
        :rtype: List[int]
        """
        def find(e,tags):
            if tags[e]==-1: return e
            else:
                tags[e]=find(tags[e],tags)
            return  tags[e]
        tags=[-1 for i in range(len(edges)+1)]
        for u,v in edges:
            root1=find(u,tags)
            root2=find(v,tags)
            if root1==root2: return [u,v]
            else: tags[root1]=root2
```
