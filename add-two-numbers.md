step1

```py

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(-1,None)
        node = dummy
        count_up = 0
        while l1 or l2 or count_up:
            l1_val = 0
            l2_val = 0
            if l1 is not None:
                l1_val = l1.val
                l1 = l1.next
            if l2 is not None:
                l2_val = l2.val
                l2 = l2.next
            total_val = l1_val + l2_val + count_up
            count_up = total_val // 10
            node_val = total_val % 10
            node.next = ListNode(node_val,None)
            node = node.next
        return dummy.next
             
```
感想　
仕組み自体は簡単でやり方は頭でわかっているのに、うまく表現ができなくて非常に悔しい。
変数名も不適当だと感じることが多々あるので、2回目は他の人の解答パターンをたくさん見て参考にしたい。