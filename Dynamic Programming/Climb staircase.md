# Climb staircase 
> Climb one or two ladder each time, how many paths for a given number of staircase
```
def climb(n):
    dp=[0]* n
    dp[0],dp[1]=1,2
    for i in range(2,n):
        dp[i]=dp[i-1]+dp[i-2]# current situation only changed by last situation before it, other situation have no effect
    dp[-1]
```

```
def climb_improve(n):
    first=1
    second=2
    for i in range(2,n):
        third=first+second # roll array
        first=second# roll array
        second=third
    return third
```
## If the question only consider current situation and few number of situaions not all situations. we can use roll array instead of whole DP array.
