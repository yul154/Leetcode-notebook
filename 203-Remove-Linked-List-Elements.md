> Remove all elements from a linked list of integers that have value val.

# Example:
Input:  1->2->6->3->4->5->6, val = 6

Output: 1->2->3->4->5

# Code
```
dummy=ListNode(0)
dummy.next=head
cur=dummy
while cur and cur.next:
     if cur.next.val==val:
        cur.next=cur.next.next
     else:
        cur=cur.next
return dummy.next        
```
```
dummy=ListNode(0)
dummy.next=head
pre=dummy
while head:
      if head.val==val:
         pre.next=head.next
      else:
         pre=pre.next
       head=head.next
return dummy.next
```

Mark points:
1. head: just a node not rest of linked list
2. if else is different with just if : only use if , rest of code will use the result from if 
