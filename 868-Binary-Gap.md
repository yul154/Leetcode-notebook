>Given a positive integer N, find and return the longest distance between two consecutive 1's in the binary representation of N. If there aren't two consecutive 1's, return 0.\

# Example
Input: 22

Output: 2

Explanation: 

22 in binary is 0b10110.

In the binary representation of 22, there are three ones, and two consecutive pairs of 1's.

The first consecutive pair of 1's have distance 2.

The second consecutive pair of 1's have distance 1.

The answer is the largest of these two distances, which is 2.

# Code
```
def binaryGap(self, N):
        """
        :type N: int
        :rtype: int
        """
        maks=0
        lst=[]
        binary =bin(N)[2:]
        for i in range(len(binary)):
            if binary[i]=='1':
                lst.append(i)
        for j in range(len(lst)):
            if len(lst)<=1:
                maks=0
            elif lst[j]-lst[j-1]>maks:
                maks=lst[j]-lst[j-1]
        return maks
```
