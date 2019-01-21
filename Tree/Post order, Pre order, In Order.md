# Preorder
```
def preorder1(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res=[]
        def dfs(node,lst):
            if node:
                res.append(node.val)
                for i in node.children:
                    dfs(i,lst)
            return lst
        
        return dfs(root,res)
        
def preorder(self, root):
        res=[]
        if root:
            res.append(root.val)
            for i in root.children:
                res+=self.preorder(i)
        return res
```
# Postorder
```
def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res=[]
        def postorder(node,lst):
            if not node:
                return lst
            for i in node.children:
                postorder(i,lst)
            lst.append(node.val)
            return lst
        return postorder(root,res)
        
def postorder(self,root):
        res=[]
        if root:
            stack=[root]
            while stack:
                cur=stack.pop()
                if cur:
                    res.append(cur.val)
                for i in cur.children:
                    stack.append(i)
        return res[::-1]           
```

# Inorder
```
def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res=[]
        if root:
            res+=self.inorderTraversal(root.left)
            res.append(root.val)
            res+=self.inorderTraversal(root.right)
        return res
        
def inorderTraversal(self, root):
        res,stack=[],[]
        while root or stack:
            while root:
                stack.append(root)
                root=root.left
            root=stack.pop()
            res.append(root.val)
            root=root.right
        return res
                    
```
