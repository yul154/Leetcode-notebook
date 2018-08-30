> A self-dividing number is a number that is divisible by every digit it contains.For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0. Also, a self-dividing number is not allowed to contain the digit zero.Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

# Example
Input: 

left = 1, right = 22

Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]

# Code:
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
# Code2
```
def check(num):
    digits = set(map(int, str(num)))
    if 0 in digits: 
        return False
    return not any(num % d for d in digits)
return filter(check, range(left, right + 1)) 
```
# Mark points
1. str are letter sequence
2. compare `filter()` with `map()`:
    * `map()`: apply function to every item in the sequence, and return an interator of results
    * `filter()`: functions as a filter to filter 'True' item and return a new list of them
```
    L1=list(filter(lambda n:n%2==1,range(1,20)))
    L2=list(map(lambda n:n%2==1,range(1,20)))
```
3. `reduce()`: return a single value which is cumulation from left to right.
 `reduce(lambdax,y:x+y,range(20))`
4. List comprehension:[expression(variable) for variable in input_set [predicate][, …]]
 `[n for n in [1, 2, 3] if n % 2]`
5. `any`: Returns a Boolean value that indicates whether the collection contains any values that evaluate to True which means not '',0 and False
6. `joint`：Returns a string made from the elements of an iterable.
 `print(list(n for n in ''.join(['abc','de']])))`
 `print(word[i] for words in ['abc','de'] for i in range(len(words)))`
