>Alice and Bob have candy bars of different sizes: A[i] is the size of the i-th bar of candy that Alice has, and B[j] is the size of the j-th bar of candy that Bob has.

>Since they are friends, they would like to exchange one candy bar each so that after the exchange, they both have the same total amount of candy.  (The total amount of candy a person has is the sum of the sizes of candy bars they have.)

>Return an integer array ans where ans[0] is the size of the candy bar that Alice must exchange, and ans[1] is the size of the candy bar that Bob must exchange.

>If there are multiple answers, you may return any one of them.  It is guaranteed an answer exists.

# Example

Input: A = [1,2,5], B = [2,4]
Output: [5,4]

# Code

```
b=set(B)
middle=(sum(A)+sum(B))/2
k=middle - sum(A)
for i in A:
    if i+k in b:
       return [i,i+k]
```
```
b=set(B)
middle=(sum(A)+sum(B))/2
for i in A:
    j=middle-(sum(A)-i)
    if j in b:
       return [i,j]
```
# Mark points
1. don't care about the key is positive or negative
