> Given a positive integer, check whether it has alternating bits: namely, if two adjacent bits will always have different values.

# Example
Input: 7
Output: False
Explanation:
The binary representation of 7 is: 111.

# Code:
```
binary=bin(n)[2:]
        return all(binary[x]!=binary[x+1] for x in range(len(binary)-1))
```
