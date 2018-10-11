> Given two arrays, write a function to compute their intersection.
# Example:
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]

# Code
```
s=set()
for i in nums1:
      if i in nums2:
            s.add(i)
return list(s)
```
```
list(set(nums1) & set(nums2))
```
# mark points
* bitwise operations
1. `&`: intersection
2. `|`: combination
3. `^`:XOR
