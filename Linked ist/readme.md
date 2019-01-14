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
pre,cur=None,head
while cur:
    cur.next,pre,cur=pre,cur,cur.next
```
## Slow, faster pointers
```
def detectCycle1(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        maping=set()
        dummy=head
        while dummy:
            if dummy in maping:
                return dummy     
            maping.add(dummy)
            dummy=dummy.next
        return None
    
def detectCycle2(self, head):
    slow=fast=head
    while fast and fast.next:
        slow=slow.next
        fast=fast.next.next
        if slow == fast:
            break
    else:
        return None
    while head!=slow:
        head=head.next
        slow=slow.next
    return head
def detectCycle(self, head):
    track=head
    while track:
        if isinstance(track.val,str):
            return track
        track.val=str(track.val)
        track=track.next
    return None
```

