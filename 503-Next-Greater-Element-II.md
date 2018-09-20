>Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.

#  Example
Input: [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number; 
The second 1's next greater number needs to search circularly, which is also 2.

# Code
```
def nextGreaterElements(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        stack=[]
        size=len(nums)
        ans=[-1]*size
        for i in range(size*2):
            j=i%size
            while stack and nums[stack[-1]]<nums[j]:
                ans[stack.pop()]=nums[j]
            stack.append(j)
        return ans
```

Mark point:
1. loop twice:
```
for i in range(size*2):
            j=i%size
```
