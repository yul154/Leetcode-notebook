>On a N * N grid, we place some 1 * 1 * 1 cubes.

>Each value v = grid[i][j] represents a tower of v cubes placed on top of grid cell (i, j).

>Return the total surface area of the resulting shapes.

# Example
Input: [[2]]
Output: 10
Input: [[1,2],[3,4]]
Output: 34
Input: [[1,1,1],[1,0,1],[1,1,1]]
Output: 32

# Code
```
area=0
n=len(grid)
for i in range(n):
    for j in range(n):
        if grid[i][j]: area+=grid[i][j]*4+2
        if j: area-=min(grid[i][j],grid[i][j-1])*2
        if i: area-=min(grid[i][j],grid[i-1][j])*2
return area
```
Mark points
1. vertical order
