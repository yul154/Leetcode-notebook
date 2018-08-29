> Let's call an array A a mountain if the following properties hold:
>   * A.length >= 3
>   * There exists some 0 < i < A.length - 1 such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]

> Given an array that is definitely a mountain, return any i such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1].
# Examle
Input: [0,2,1,0]
Output: 1

# code:
```
class Solution(object):
    def peakIndexInMountainArray(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        for i in range(len(A)):
            if A[i]>A[i+1]:
                return i
```

# code2:
```
## binar search: if left number is smaller than middle, looking for right side, if right number is samller than middle, looking for left side
left, right = 0, len(A) - 1
        while left < right:
            mid = (left + right) / 2
            if A[mid - 1] < A[mid] and A[mid] < A[mid + 1]:
                left = mid
            elif A[mid - 1] > A[mid] and A[mid] > A[mid + 1]:
                right = mid
            else:
                break
        return mid
   
```
