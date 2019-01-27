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

# 208
```
class Trie(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.root={}
        

    def insert(self, word):
        """
        Inserts a word into the trie.
        :type word: str
        :rtype: void
        """
        cur=self.root
        for char in word:
            if char not in cur:
                cur[char]={}
                cur=cur[char]
            else:
                cur=cur[char]
        cur['#']='True'

        

    def search(self, word):
        """
        Returns if the word is in the trie.
        :type word: str
        :rtype: bool
        """
        cur=self.root
        for char in word:
            if char not in cur:
                return False
            cur=cur[char]
        return "#" in cur

        

    def startsWith(self, prefix):
        """
        Returns if there is any word in the trie that starts with the given prefix.
        :type prefix: str
        :rtype: bool
        """
        cur=self.root
        for char in prefix:
            if char not in cur:
                return False
            cur=cur[char]
        return True
```
# 745
* Using dictionary
```
class WordFilter:
    def __init__(self, words):
        """
        :type words: List[str]
        """
        self.root={}
        for idx,word in enumerate(words):
            for pre in range(len(word)+1):
                prefix=word[:pre]
                for suf in range(len(word)+1):
                    suffix=word[suf:]
                    self.root[(prefix,suffix)]=idx
 
    def f(self, prefix, suffix):
        """
        :type prefix: str
        :type suffix: str
        :rtype: int
        """
        return self.root.get((prefix,suffix),-1)
```
* Using trie
```
from collections import defaultdict
Trie= lambda: defaultdict(Trie)
W=None
class WordFilter:

    def __init__(self, words):
        """
        :type words: List[str]
        """
        self.pre=Trie()
        self.suf=Trie()
        for w,word in enumerate(words):
            cur=self.pre
            self.addw(cur,w)
            for char in word:
                cur=cur[char]
                self.addw(cur,w)
            cur=self.suf
            self.addw(cur,w)
            for char in word[::-1]:
                cur=cur[char]
                self.addw(cur,w)
    def addw(self,node,w):
        if W not in node:
            node[W]={w}
        else:
            node[W].add(w)

    def f(self, prefix, suffix):
        """
        :type prefix: str
        :type suffix: str
        :rtype: int
        """
        cur1=self.pre
        for char in prefix:
            if char not in cur1: return -1
            cur1=cur1[char]
        cur2=self.suf
        for char in suffix[::-1]:
            if char not in cur2: return -1
            cur2=cur2[char]
        return max(cur1[W]&cur2[W])
```

# 648
```
 class Trie():
    def __init__(self):
        self.root={}
    def insert(self,word):
        cur=self.root
        for char in word:
            if char not in cur:
                cur[char]={}
            cur=cur[char]
        cur['#']=word
    def replace(self,word):
        cur=self.root
        for char in word:
            if char not in cur:
                return word
            cur=cur[char]
            if cur.get('#'):return cur['#']
        return word
class Solution:
    def replaceWords(self, dict, sentence):
        """
        :type dict: List[str]
        :type sentence: str
        :rtype: str
        """
        trie=Trie()
        for word in dict:
            trie.insert(word)
        words=sentence.split(' ')
        for i in range(len(words)):
            words[i]=trie.replace(words[i])
        
        return ' '.join(words)
```
