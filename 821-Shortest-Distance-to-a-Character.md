> Given a string S and a character C, return an array of integers representing the shortest distance from the character C in the string.

#Example
Input: S = "loveleetcode", C = 'e'
Output: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]

# Code
```
class Solution(object):
    def shortestToChar(self, S, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        index=list(range(len(S)))
        mark=[]
        SD=[]
        for i in range(len(S)):
            if S[i]==C:
                mark.append(i)
        for j in index:
             SD.append(min(map(lambda x:abs(x-j),mark)))
        
        return SD
```
