> Consider all the leaves of a binary tree.  From left to right order, the values of those leaves form a leaf value sequence.

# Code
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        def leaflist(root):
            if not root:
                return []
            elif not root.left and not root.right:
                return [root.val]
            else:
                return leaflist(root.left)+leaflist(root.right)
            
        return list(leaflist(root1))==list(leaflist(root2))     
```
