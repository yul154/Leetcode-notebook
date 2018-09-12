>A website domain like "discuss.leetcode.com" consists of various subdomains. At the top level, we have "com", at the next level, we have "leetcode.com", and at the lowest level, "discuss.leetcode.com". When we visit a domain like "discuss.leetcode.com", we will also visit the parent domains "leetcode.com" and "com" implicitly.Now, call a "count-paired domain" to be a count (representing the number of visits this domain received), followed by a space, followed by the address. An example of a count-paired domain might be "9001 discuss.leetcode.com". We are given a list cpdomains of count-paired domains. We would like a list of count-paired domains, (in the same format as the input, and in any order), that explicitly counts the number of visits to each subdomain.

#Example
Input: 
["900 google.mail.com", "50 yahoo.com", "1 intel.mail.com", "5 wiki.org"]
Output: 
["901 mail.com","50 yahoo.com","900 google.mail.com","5 wiki.org","5 org","1 intel.mail.com","951 com"]
Explanation: 
We will visit "google.mail.com" 900 times, "yahoo.com" 50 times, "intel.mail.com" once and "wiki.org" 5 times. For the subdomains, we will visit "mail.com" 900 + 1 = 901 times, "com" 900 + 50 + 1 = 951 times, and "org" 5 times.

# Code
```
from collections import Counter
class Solution(object):
    def subdomainVisits(self, cpdomains):
        """
        :type cpdomains: List[str]
        :rtype: List[str]
        """
        ans=  Counter()
        for domain in cpdomains:
                count, domain = domain.split()# put into two different variables
                count = int(count)
                frag=domain.split('.')
                for i in range(len(frag)):
                        ans[".".join(frag[i:])]+=count
        return ["{} {}".format(c,d) for d,c in ans.items()]
```
# Code2
```
domain_counts = defaultdict(int)
for i in n:
    times, domains = i.split()
    times = int(times)
    domain_counts[domains] += times
    while '.' in domains:
                domains = domains[domains.index('.') + 1:]
                domain_counts[domains] += times
print ([str(v) + ' ' + d for d, v in domain_counts.items()])
```
# Code3
```
a=[]
b=[]
c=[]
s=[]
dic={}
for i in n:
        st,num = i.split()
        a.append(st)
        b.append(num)
for i in b:
    c.append(i.split('.'))
for i in range(len(a)):
    c[i].insert(0,a[i])

for i in c:
        for j in range(1, len(i)):
            m = '.'.join(i[j:])
            if m not in dic:
                dic[m] = int(i[0])# add value to key
            else:
                dic[m] += int(i[0])
for key,value in dic.items():
    x=str(value)+' '+key
    s.append(x)
return(s)
```

# Mark points
1. Counter():A Counter is a container that keeps track of how many times equivalent values are added. 
  * `update()` method can add element to a Counter
  * `elements()` method returns an iterator that produces all of the items known to the Counter
    * The order of elements is not guaranteed, and items with counts less than zero are not included
2. index():Returns the index of the last occurrence of the string searched for

