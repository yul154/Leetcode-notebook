> Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

# Example:
Input: [9,6,4,2,3,5,7,0,1]

Output: 8

# Code
```
dic={}
nums=nums+list(range(len(nums)+1))
for i in nums:
    dic[i]=dic.get(i,0)+1
for k,v in dic.items():
     if v==1:
        return k
```

```
for i in range(len(nums)):
    if i !=nums[i]:
        return i
return i+1
```
```
dissum=len(n)*(len(n)-1)/2
sum=sum(n)
dissum-sum
```
```
res^=i^n[i]
```

Mark points:
1. `set1`-`set2`:return element in set1 which not in set2
2. 4∧(0∧0)∧(1∧1)∧(2∧3)∧(3∧4):2
