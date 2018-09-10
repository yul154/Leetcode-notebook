> Given a n-ary tree, find its maximum depth. The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

# Code

```
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Node
        :rtype: int
        """
        count=0
        if not root:
            return 0
        elif not root.children:
            return 1
        depth=1+max(self.maxDepth(child) for child in root.children)
        return depth
```

DFS?????
