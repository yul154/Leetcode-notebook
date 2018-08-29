> A self-dividing number is a number that is divisible by every digit it contains.For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0. Also, a self-dividing number is not allowed to contain the digit zero.Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

# Example
Input: 

left = 1, right = 22

Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]

# code:
```
class Solution(object):
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        lst=[]
        for i in list(range(left,right+1)):
            for r in str(i):
                if r=='0' or i %int(r) > 0:
                    lst.append(i) 
                else:
                    continue  
                    
        l=[x for x in list(range(left,right+1)) if x not in lst]
        return l
```
# code2
```
def check(num):
    digits = set(map(int, str(num)))
    if 0 in digits: 
        return False
    return not any(num % d for d in digits)
return filter(check, range(left, right + 1)) 
```
M
