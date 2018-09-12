>You're now a baseball game point recorder. Given a list of strings, 
>* each string can be one of the 4 following types:
>1. Integer (one round's score): Directly represents the number of points you get in this round
>2. "+" (one round's score): Represents that the points you get in this round are the sum of the last two valid round's points.
>3. "D" (one round's score): Represents that the points you get in this round are the doubled data of the last valid round's points.
>4. "C" (an operation, which isn't a round's score): Represents the last valid round's points you get were invalid and should be removed.

>Each round's operation is permanent and could have an impact on the round before and the round after.

>You need to return the sum of the points you could get in all the rounds.

# Example
Input: ["5","-2","4","C","D","9","+","+"]
Output: 27
Explanation: 
Round 1: You could get 5 points. The sum is: 5.
Round 2: You could get -2 points. The sum is: 3.
Round 3: You could get 4 points. The sum is: 7.
Operation 1: The round 3's data is invalid. The sum is: 3.  
Round 4: You could get -4 points (the round 3's data has been removed). The sum is: -1.
Round 5: You could get 9 points. The sum is: 8.
Round 6: You could get -4 + 9 = 5 points. The sum is 13.
Round 7: You could get 9 + 5 = 14 points. The sum is 27.
# Code
```
class Solution(object):
    def calPoints(self, ops):
        """
        :type ops: List[str]
        :rtype: int
        """
        lst=[]
        count=0
        opss=[]
        for i in ops:
            if i.isdigit():
                opss.append(int(i))
            elif i.lstrip('-').isdigit():
                opss.append(int(i))
            else:
                opss.append(i)  
        for i in range(len(opss)):
            if type(opss[i]) is int:
                lst.append(int(opss[i]))
                count+=opss[i]
            elif opss[i] =='C':
                count-=lst.pop()
            elif ops[i]=='+':
                count+=lst[-1]
                count+=lst[-2]
                lst.append(lst[-1]+lst[-2])
            elif opss[i]=='D':
                count+=int(2*lst[-1])
                lst.append(2*lst[-1])
        return count
```
# Code2
```
def calPoints(self, ops):
        """
        :type ops: List[str]
        :rtype: int
        """
        s = []
        for op in ops:
            if op == "+": s += [s[-1] + s[-2]]
            elif op == "C": s = s[:-1]
            elif op == "D": s += [s[-1]*2]
            else: s += [int(op)]
        
        return sum(s)

```

Mark points:
1. `isdigit()`:Returns a Boolean stating whether the string contains only digits.
2. `lstrip([string])` and 'rstrip([string])':Returns a copy of the string with leading characters removed.
