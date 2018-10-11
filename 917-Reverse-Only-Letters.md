> Given a string S, return the "reversed" string where all characters that are not a letter stay in the same place, and all letters reverse their positions.
# Example
Input: "ab-cd"
Output: "dc-ba"

Input: "a-bC-dEf-ghIj"
Output: "j-Ih-gfE-dCba"

# Code
```
lst=OrderedDict()
b=''
for i in range(len(S)):
    if S[i].isalpha():
        b+=''.join(S[i])
    else:
        lst[i]=S[i]
c=b[::-1]
for i in lst.keys():
    c=c[:i]+lst[i]+c[i:]
return c
```

```
lst=[]
for s in S:
    if s.isalpha():
       lst.append(s)
res=''
for s in S:
     if s.isalpha():
        res+=lst.pop()
     else:
        res+=s
return res
```
```
l=len(S)-1
res=''
for i in S:
    if i.isalpha():
        while not S[l].isalpha():
              l-=1
    res+=S[l]
    l-=1
    else:
         res+=i
return res
```

# Mark points
1. `isalpha()`: Returns a Boolean stating whether the string contains only letters.
2. `OrderedDict()`:a dictionary subclass that remembers the order in which its contents are added.
3. `insert(index,content)`
4. `add()`:only for set
