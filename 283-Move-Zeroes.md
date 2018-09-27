> Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

#  Example
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]

# Code
```
for i in nums:
    if i ==0:
       nums.remove(i)
       nums.append(i)
# Runtime: 16 ms
```

```
zero=0
for i in range(len(nums)):
    if nums[i]!=0:
       nums[i],nums[zero]=nums[zero],nums[i]
       zero+=1
# Runtime: 24 ms
```
```
nums.sort(key = lambda x: 1 if x == 0 else 0)
# Runtime: 24 ms
```

Mark points:
1. `list. sort([cmp[, key[, reverse]]])`
  * key：Specifies a function of one argument that is used to extract a comparison key from each list element. The default value is None
  * cmp:cmp parameter, which determines the sort order. The argument for cmp is a function that, like all cmp-style functions, returns a negative, zero, or positive result depending on the order of its two arguments.
2. difference between `sort()` and `sorted()`:
  * `sort()`: reorder original list
  * `sorted()`: make a new list
