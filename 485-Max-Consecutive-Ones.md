> Given a binary array, find the maximum number of consecutive 1s in this array.

# Example

Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
# Code

```
lst=[]
count=0
for i in nums:
    if i==1:
       count+=1
       lst.append(count)
    else:
        count=0
        lst.append(i)
return max(lst)
```
```
s = ''.join(str(i) for i in nums)
l = s.split('0')
ln = []
for i in l:
    ln.append(len(i))
return max(ln)
```
```
ans = cnt = 0
for n in nums:
    if n == 1:
       cnt += 1
       ans = max(ans, cnt)
    else:
       cnt = 0
return ans
```

# mark points
1. renew max: make a temporary max and max(temp, current)
