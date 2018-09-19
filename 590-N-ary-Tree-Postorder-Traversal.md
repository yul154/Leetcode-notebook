> Given an n-ary tree, return the postorder traversal of its nodes' values.
# Code
```
def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res=[]
        if not root:
            return res
        else:
            for i in root.children:
                res.extend(self.postorder(i))
            res.append(root.val)
        return res
```

Mark points:
1. `list.extend()`:appending all the items from the iterable
2.  VS `append()`:appends an object to the end of the list VS appends each element of the iterable object
3. `extend()` ≈`+=`
