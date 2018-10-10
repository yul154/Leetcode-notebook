> Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] 
> and the absolute difference between i and j is at most k.

#  Example
Input: nums = [1,2,3,1], k = 3

Output: true

Input: nums = [1,2,3,1,2,3], k = 2

Output: false

# Code
```
if len(set(nums)) == len(nums):
           return False
for i in range(len(nums)):
    j=1
    for j in range(1,k+1):
        if j+i<len(nums) and nums[i]==nums[i+j]:
           return True
return False
```

```
location={}
for i in range(len(nums)):
    if nums[i] in location and i-location[nums[i]]<=k:
        return True
    else:
        location[nums[i]]=i
return False
```

```
window=set([])
for i in range(len(nums)):
    if i>k: window.discard(nums[i-k-1])
    if nums[i] in window: return True
    else: window.add(nums[i])
return False
```

# Mark points
1. if you want to store index of element: dictionary[list[i]]=i
2. set.discard(): remove no exist element will not raise KeyError
