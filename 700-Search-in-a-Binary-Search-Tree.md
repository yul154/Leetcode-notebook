> Given the root node of a binary search tree (BST) and a value. You need to find the node in the BST that the node's value equals the given value. Return the subtree rooted with that node. If such node doesn't exist, you should return NULL.

#Example:

Given the tree:
        4
       / \
      2   7
     / \
    1   3

And the value to search: 2

Output:
Given the tree:
      2     
     / \   
    1   3
    
 #Code
 ```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def searchBST(self, root, val):
        """
        :type root: TreeNode
        :type val: int
        :rtype: TreeNode
        """
        if not root :
            return None
        elif root.val==val:
                return root
        elif root.val<val:
            return self.searchBST(root.right,val)
        else:
            return self.searchBST(root.left,val)
 ```
 
Mark points:
1. `if not` VS `if is None`: 
  * "if not value" :check if the value is considered False (empty list, none, false).
  * 'if is None': Just identity with the None object

