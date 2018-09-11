> Write a program that outputs the string representation of numbers from 1 to n. But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

Example:
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
#Code:
```
def fizzBuzz(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        lst=[]
        for i in range(1,n+1):
            if i%3==0 and i%5==0:
                lst.append("FizzBuzz")
            elif i%3==0:
                lst.append('Fizz')
            elif i%5==0:
                lst.append('Buzz')
            else:
                lst.append(str(i))
        return lst
```

```
return [str(i) if (i%3!=0 and i%5!=0) else (('Fizz'*(i%3==0)) + ('Buzz'*(i%5==0))) for i in range(1,n+1)]

```
