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
 ```
## 547
## 684
