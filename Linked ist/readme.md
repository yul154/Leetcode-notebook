# Pros
## Easily operate on Head node(insert, delete) without changes of rest
```
dummy=ListNode(0)
dummy.next=head
curr=head
```
## Reverse list: need pre,cur two pointers
```
pre=None
cur=head
while cur:
    new=cur.next
    cur.next=pre
    pre=cur
    cur=new
```

```
second=head.next
head.next=None
rest=self.reverse(seconds)
second.next=head
return rest
```
## Slow, faster pointers

