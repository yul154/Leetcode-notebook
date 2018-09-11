> A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element. Now given an M x N matrix, return True if and only if the matrix is Toeplitz.
 
 # Example:
 Input:
matrix = [
  [1,2,3,4],
  [5,1,2,3],
  [9,5,1,2]
]
Output: True
Explanation:
In the above grid, the diagonals are:
"[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]".
In each diagonal all elements are the same, so the answer is True.

# Code:
```
class Solution(object):
    def isToeplitzMatrix(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: bool
        """
        for i in range(1,len(matrix)):
            for j in range(1,len(matrix[0])):
                if matrix[i][j]!=matrix[i-1][j-1]:
                           return False
        return True
        
return all(r == 0 or c == 0 or matrix[r-1][c-1] == val
                   for r, row in enumerate(matrix)
                   for c, val in enumerate(row))
```
# Code 2
```
return all(matrix[r][:-1]==matrix[r+1][1:] for r in range(len(matrix)-1)

```
# Code3
```
groups={}
for r, row in enumerate(matrix):
    for c,val in enumerate(row):
        print(r,c,row,val)
        if r-c not in groups:
            groups[r-c]=val
        elif groups[r-c]!=val:
            return False
return True
```
Mark points:
1. Return True on the end of program: if all conditions are met
2. `all()`: no False, return True, have False ,return False
3. `enumerate`:`enumerate (sequence, start=0)`
    * returns a tuple containing a count (from start which defaults to 0) and the values obtained from iterating over sequence
