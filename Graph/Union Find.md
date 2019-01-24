# Union Find

* Dynamic connectivity of a list of node
  * DC: afte union a new node ,detech groups
* Using in undirect grpah

## algorthim:
  1. build n groups
  2. traversal nodes and figure out which group they belong to(find)
  3. if they are not in a same group, union(union)
  4. if in a sam group, pass
```
tags=[i for i in range(n)]

def find(e,tags):
    if tags[e]==e:
      return True
    else:
      find(tags[e],tags)# find an ancestor

def union(e1,e2):
    root1=find(e1,tags)
    root2=find(e2,tags)
    if root1==root2:
      return 
    else:
      tag[root2]=root1
```

# 399
# 684
