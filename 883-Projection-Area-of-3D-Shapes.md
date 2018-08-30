> On a N * N grid, we place some 1 * 1 * 1 cubes that are axis-aligned with the x, y, and z axes.Each value v = grid[i][j] represents a tower of v cubes placed on top of grid cell (i, j).Now we view the projection of these cubes onto the xy, yz, and zx planes. A projection is like a shadow, that maps our 3 dimensional figure to a 2 dimensional plane. Here, we are viewing the "shadow" when looking at the cubes from the top, the front, and the side. Return the total area of all three projections.

# Example 

Input: [[1,2],[3,4]]
Output: 17
Input: [[1,1,1],[1,0,1],[1,1,1]]
Output: 14

#Code
```
class Solution(object):
    def projectionArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        xy=0#sum(all element without 0)
        xz=0#sum(max(each list))
        yz=0#sum(max(each index )) 
        xy= sum(i>0 for j in grid for i in j )# no zero numbers
        xz= sum(list(map(lambda x: max(x), grid)))# max value in each sublist
        yz=sum(list(map(lambda x: max(x), zip(*grid))))# max value in same position of each sublist
        x=xy+xz+yz
        return x
```
# Mark points:
1. `*`: when the arguments are already in a list or tuple but need to be unpacked for a function call requiring separate positional arguments
```
>>> a=[[1,2,3],[4,5,6]]
>>> list(zip(*a))
[(1, 4), (2, 5), (3, 6)]
````
