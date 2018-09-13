>You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.
# Example
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16

# Code
```
count=0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j]==1:
                    count+=4
                    if grid[i-1][j] and i>0:
                        count-=2
                    if grid[i][j-1] and j>0:
                        count-=2
        return count
        
```
Mark points:
1. if pass:just do nothing
2. if continue: continue passes for the next iteration of the for loop
3. if var:
    * Booleans are numeric values.  0 is usually the only value that evaluates to false
    * Any non-null reference evaluates to true, null references evaluate to false.
