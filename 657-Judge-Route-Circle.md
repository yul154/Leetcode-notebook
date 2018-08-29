> Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to the original place.The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are R (Right), L (Left), U (Up) and D (down). The output should be true or false representing whether the robot makes a circle.

# Example
Input: "UD"
Output: true

# Code
```
class Solution(object):
    def judgeCircle(self, moves):
        """
        :type moves: str
        :rtype: bool
        """
        return moves.count('L') == moves.count('R') and moves.count('U') == moves.count('D')
            
   def judgeCircle(self, moves):# Solution 2
        """
        :type moves: str
        :rtype: bool
        """
        left_right=0
        down_up=0
        for i in range(len(moves)):
            if(moves[i]=='R'):  left_right=left_right+1
            if (moves[i] == 'L'):  left_right = left_right - 1
            if(moves[i]=='U'):  down_up=down_up+1
            if(moves[i]=='D'):  down_up=down_up-1
        if(left_right==0 and down_up==0):return True
        else: return False
          
```

# Mark points

1.raises a `KeyError` whenever a dict() object is requested (using the format a = adict[key]) and the key is not in the dictionary.
