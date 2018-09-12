> An array is monotonic if it is either monotone increasing or monotone decreasing.An array A is monotone increasing if for all i <= j, A[i] <= A[j].  An array A is monotone decreasing if for all i <= j, A[i] >= A[j]. Return true if and only if the given array A is monotonic.

# Example
Input: [6,5,4,4]
Output: true

Input: [1,2,4,5]
Output: true

# Code:
```
class Solution(object):
    def isMonotonic(self, A):
        """
        :type A: List[int]
        :rtype: bool
        """        
        def increase(A):
            return all(A[i]>=A[i-1] for i in range(1,len(A)))
        def decrease(A):
            return all(A[i]<=A[i-1] for i in range(1,len(A)))
        return increase(A) or decrease(A)
```
# Mark points
1. `np.differe()`: get a list which difference between elements in other list

