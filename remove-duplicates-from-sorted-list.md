```py

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        current_pointer = head
        while current_pointer is not None and current_pointer.next is not None:
            if current_pointer.val == current_pointer.next.val:
                current_pointer.next = current_pointer.next.next
            else:
                current_pointer = current_pointer.next
        return head

```

感想
循環しないリストなので素直に処理が書けると思いました。
当初は変数next_pointerを宣言していたため、逆に見づらくなってしまった。
変数はむやみに増やせばいいのではなく、今回はどこを始点としているかという観点があると
コードが読みやすくなると思いました。

参照：
https://github.com/t-ooka/leetcode/pull/10
https://github.com/nanae772/leetcode-arai60/pull/4

