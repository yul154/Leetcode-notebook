> Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

# Example
Input: [4,1,2,1,2]
Output: 4

# Code
```
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count=dict()
        for i in nums:
            count[str(i)]=count.get(str(i),0)+1
        
        target=[key for key, value in count.iteritems() if value == 1]
        
        return int(target[0])
```
