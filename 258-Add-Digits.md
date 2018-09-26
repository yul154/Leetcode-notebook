> Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

# Example:
Input: 38

Output: 2 

Explanation: The process is like: 3 + 8 = 11, 1 + 1 = 2. 
             Since 2 has only one digit, return it.

# Code
```
while num>9:
      s=0
while num>0:
      s+=num%10
      num=num//10
      num=s
return num
```
```
if num==0:
   return 0
elif num%9==0:
   return 9
else:
   return num%9
```
Mark points:
1. digit root:It helps to see the digital root of a positive integer as the position it holds with respect to the largest multiple of 9 less than the number itself.
