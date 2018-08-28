>The Hamming distance between two integers is the number of positions at which the corresponding bits are different.
>Given two integers x and y, calculate the Hamming distance.

# Example
Input: x = 1, y = 4
Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑
The above arrows point to positions where the corresponding bits are different.

# code
```
class Solution(object):
    def hammingDistance(self, x, y):
        """
        :type x: int
        :type y: int
        :rtype: int
        """
        bx='{0:032b}'.format(x)#bx = bin(x)[2:],bx = bx.zfill(32)
        by='{0:032b}'.format(y)#by = bin(y)[2:],by = by.zfill(32)
        diff=0
        for x in range(32):
            if bx[x]!=by[x]:
                diff+=1
        return diff
```

# Mark points
1. `{0:032b}`
