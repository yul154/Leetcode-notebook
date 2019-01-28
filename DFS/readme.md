# DFS
```
def DFS1(v,h,grid):
   if v<0 or h<0 or v>=len(grid) or h>=len(grid[0]) or grid[v][h]!='1':
       return
   grid[v][h]='-1'
   DFS(v+1,h,grid)
   DFS(v,h+1,grid)
   DFS(v-1,h,grid)
   DFS(v,h-1,grid)
```

# BFS
```
def bfs(i,j,grid):
    grid[i][j]='0'
    q=deque([(i,j)])
    moves=[(1,0),(0,1),(-1,0),(0,-1)]
    while q:
        cr,cl=q.popleft()
        for a,b in moves:
            nr,nl=cr+a,cl+b
            if 0<=nr<len(grid) and 0<=nl<len(grid[0]) and grid[nr][nl]=='1':
                q.append((nr,nl))
                grid[nr][nl]='0' 
```
