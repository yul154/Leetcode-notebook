>The count-and-say sequence is the sequence of integers with the first five terms as following:

>1.     1
>2.     11
>3.     21
>4.     1211
>5.     111221
>1 is read off as "one 1" or 11.

>11 is read off as "two 1s" or 21.

>21 is read off as "one 2, then one 1" or 1211.

>Given an integer n where 1 ≤ n ≤ 30, generate the nth term of the count-and-say sequence.

>Note: Each term of the sequence of integers will be represented as a string.

# Example:
Input: 4
Output: "1211"

# Code:
```
res = '1'
for i in range(n-1):
    res = ''.join([str(len(list(group))) + digit for digit, group in itertools.groupby(res)])
return res
```
```

```
# Mark points
1. `from itertools import groupby`:Make an iterator that returns consecutive keys and groups from the iterable.
  * The key is a function computing a key value for each element. If not specified or is None
```
[k for k, g in groupby('AAAABBBCCDAABBB')] --> A B C D A B
[list(g) for k, g in groupby('AAAABBBCCD')] --> AAAA BBB CC D
```
