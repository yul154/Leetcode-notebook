>Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.

>You may return any answer array that satisfies this condition.

#  Example
Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.

# Code
```
def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        """lst=[]
        lst1=[]
        for i in A:
            if i%2==0:
                lst.append(i)
            else:
                lst1.append(i)
        return lst+lst1
        """
        return sorted(A,key=lambda x: x%2)
```
Mark points
1. `sorted(iterable[, cmp[, key[, reverse]]])`:
  1. cmp(optional):A custom comparison function of two arguments (iterable elements) which should return a negative, zero or positive number depending on whether the first argument is considered smaller than, equal to, or larger than the second argument. The default value is None.
  2. key(optional): function that serves as a key for the sort comparison
  3. reverse(optional):If true, the sorted list is reversed (or sorted in Descending order)
```
>>> sorted(['pear', 'apple', 'pineapple'], cmp=lambda x, y: cmp(len(x), len(y)))
['pear', 'apple', 'pineapple']
 ```
 ```
>>> sorted(((9, ), (1, 2, 3), (1, 2)), key=lambda x: sum(x))
[(1, 2), (1, 2, 3), (9,)]
 ```
 ```
>>> sorted({1, 3, 2}, reverse=True)
[3, 2, 1]
 ```
  
