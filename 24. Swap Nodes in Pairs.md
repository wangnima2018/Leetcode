


<h3>题意<h3>
<p>给一个链表，把每两个元素进行交换一下<p>


<h3>解题<h3>
<p>主要需要弄清楚，每一步，需要移动哪几个link之间的相互关系<p>


<h3>细节<h3>
<p>使用dummy node作为第一个node，每次判断边界条件：if pre.next is None or pre.next.next is None:
和：while cur is not None and next is not None:<p>



```python
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        if head is None or head.next is None:
            return head
        
        dummy = ListNode(0)
        dummy.next = head
        
        pre = dummy
        cur = head
        next = head.next
        
        while cur is not None and next is not None:
            nextnext = next.next
            pre.next = next
            next.next = cur
            cur.next = nextnext
            pre = cur
            if pre.next is None or pre.next.next is None:
                break
            cur = pre.next
            next = cur.next
        
        head = dummy.next
        dummy.next = None
        return head
```
