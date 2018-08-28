> Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

# Example:
Input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
Output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Explanation: First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]

# code
```
class Solution(object):
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        h=[]
        for x in A:
            h.append(x[::-1])

        for l in h:
            for n in range(len(l)) :
                l[n]=1-l[n]
        return h

"""
rows = len(A)
        cols = len(A[0])
        for row in range(rows):
            A[row] = A[row][::-1]
            for col in range(cols):
                A[row][col] ^= 1
        return A
"""
```
M
