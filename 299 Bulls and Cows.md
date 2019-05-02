# descrption
You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.
Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. 
Please note that both secret number and friend's guess may contain duplicate digits.

# Example
1. 
Input: secret = "1807", guess = "7810"

Output: "1A3B"

Explanation: 1 bull and 3 cows. The bull is 8, the cows are 0, 1 and 7

2. 
Input: secret = "1123", guess = "0111"

Output: "1A1B"

Explanation: The 1st 1 in friend's guess is a bull, the 2nd or 3rd 1 is a cow.

# Code
```
def getHint(secret,guess):
        secret=list(secret)
        guess=list(guess)
        cow=0
        bull=0
        for i in range(len(secret)):
            if guess[i]==secret[i]:
                guess[i]=''
                secret[i]=''
                bull+=1
        for i in range(len(secret)):
            for j in range(len(guess)):
                if not secret[i] or not guess[j]:
                    continue
                if secret[i]==guess[j] and i!=j:
                    cow+=1
                    guess[j]=''
                    secret[i]=''
        return str(bull)+'A'+str(cow)+'B'
```
```
def getHint(self, secret: str, guess: str) -> str:
        cow=bull=0
        for i in set(secret):
            cow+=min(secret.count(i),guess.count(i))
        for i in range(len(secret)):
            if secret[i]==guess[i]:
                bull+=1
        cow-=bull
        return str(bull)+'A'+str(cow)+'B'
```
```
def getHint(self, secret: str, guess: str) -> str:
        s_c=defaultdict(int)
        g_c=defaultdict(int)
        cow=bull=0
        for i in range(len(secret)):
            if secret[i]==guess[i]:
                bull+=1
            else:
                s_c[secret[i]]+=1
                g_c[guess[i]]+=1
        for i in g_c:
            if i in s_c:
                cow+=min(g_c[i],s_c[i])
        
        return str(bull)+'A'+str(cow)+'B'
```
# Key point
* it's very hard to find out all cow in one iteration, need to filter out bull
* same letter in differnt location, `cow+=min(g_c[i],s_c[i])`


