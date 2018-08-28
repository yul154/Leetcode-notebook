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
1. `{0:032b}.format(x)`
  * {} places a variable into a string
  * The first 0 means the 0th argument to format. After the colon is the formatting, the second 0 means zero fill to 8 spaces and b for binary
  * : adds formatting options for this variable (otherwise it would represent decimal 6)
  * 32 formats the number to 32 digits zero-padded on the left
  * b converts the number to its binary representation
2. `bin()`:Returns an integer converted into a binary string.
3. `str.format()`:Returns a formatted version of the string.
```
print("Hello, {boy} and {girl}!".format(boy="John", girl="Mary"))
print("{0} love {1}!!".format("GeeksforGeeks","Geeks"))
```
