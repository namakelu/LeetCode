```py

#step1

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_node = ListNode(0)
        dummy_node.next = head
        node = dummy_node
        while node.next is not None and node.next.next is not None:
            if node.next.val == node.next.next.val:
                duplicated_val = node.next.val
                while node.next is not None and node.next.val == duplicated_val:
                    node.next = node.next.next
            else:
                node = node.next
        return dummy_node.next
        
```

感想
ポインタ数を減らした場合の別の解法で解いてみた。
計算量は変わらないが、実ステップ数は大いに増える。
理由は.nextを都度呼び出して比較するため。
解き方に対するアプローチは概ね同じなのにここまで差が出るのは驚いた。
コードを書くときに考えることがたくさんあるなと改めて感じた。
