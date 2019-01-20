# From left to root

# DFS
## need to visit all nodes in order to figure out the minimum depth
```
def minDepth1(self, root):
    if not root:
        return 0
    if not root.left or not root.right:
        return 1+self.minDepth(root.right)+ self.minDepth(root.left)
    return 1+min(self.minDepth(root.right),self.minDepth(root.left))
```

# BFS
## faster, it would be stop if detect a left in one level, don't need to visit all node
```
def minDepth(self, root):
    depth=0
    if root:
        Queue=[root]
        while Queue:
            depth+=1
            new_q=[]
            for node in Queue:
                if not node.left and not node.right:
                    return depth
                if node.left:
                    new_q.append(node.left)
                if node.right:
                    new_q.append(node.right)
            Queue=new_q
    return depth
```
# BFS with `deque`
```
def minDepth(self, root):
        depth=0
        if root:
            Queue=deque([root])
            while Queue:
                depth+=1
                size=len(Queue)
                for num in range(size):
                    cur=Queue.popleft()
                    if not cur.left and not cur.right:
                        return depth
                    if cur.left:
                        Queue.append(cur.left)
                    if cur.right:
                        Queue.append(cur.right)
                        
        return depth
```
