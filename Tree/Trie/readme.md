# Trie
> An ordered tree data structure used to store a dynamic set or associative array where the keys are usually strings
* Use to store string
* Each node might have several children nodes while the paths to different children nodes represent different characters.
* The child nodes represent will be the origin string represented by the node itself plus the character on the path.

## Present
### Dictionary
```
class TrieNode(object):
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.nodes = defaultdict(TrieNode)  # Easy to insert new node.
        self.isword = False  # True for the end of the trie

class Trie(object):
    def __init__(self):
        self.root=TrieNode()
        
    def insert(self,word):
        cur=self.root
        for char in word:
            cur=cur.nodes[char]
        cur.isword=True
    def search(self,word):
        cur=self.root
        for char in word:
            if char not in cur.nodes:
                return False
            else:
                cur=cur.nodes[char]
        return cur.isword
    def startsWith(self,prefix):
        cur=self.root
        for char in prefix:
            if char not in cur.nodes:
                return False
            else:
                cur=cur.nodes[char]
        return True
```

### Array
```
class TrieNode(object):
    def __init__(self):
        self.node=[0 for _ in range(26)]
        self.isword=False
        
class Trie(object):
    def __init__(self):
        self.root=TrieNode()
    def insert(self,word):
        cur=self.root
        for char in word:
            index=ord(char)-97
            if cur.node[index]==0:
                cur.node[index]=TrieNode()
                cur=TrieNode()
            else:
                cur=cur.node[index]
        cur.isword=True
```
