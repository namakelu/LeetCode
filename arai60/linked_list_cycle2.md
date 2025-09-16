```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow_pointer = head
        fast_pointer = head
        has_cycle = False
        while fast_pointer is not None and fast_pointer.next is not None:
            slow_pointer = slow_pointer.next
            fast_pointer = fast_pointer.next.next
            if slow_pointer is fast_pointer:
                has_cycle = True
                break

        if has_cycle is False:
            return None

        slow_pointer = head
        while slow_pointer is not fast_pointer:
            slow_pointer = slow_pointer.next
            fast_pointer = fast_pointer.next
        return slow_pointer

# Example 1:

# Input: head = [3,2,0,-4], pos = 1
# Output: tail connects to node index 1
# Explanation: There is a cycle in the linked list, where tail connects to the second node.
# Example 2:

# Input: head = [1,2], pos = 0
# Output: tail connects to node index 0
# Explanation: There is a cycle in the linked list, where tail connects to the first node.
# Example 3:

# Input: head = [1], pos = -1
# Output: no cycle
# Explanation: There is no cycle in the linked list.

# Constraints:

# The number of the nodes in the list is in the range [0, 104].
# -105 <= Node.val <= 105
# pos is -1 or a valid index in the linked-list.

```

感想
レビューいただいた内容を踏まえて修正。
(breakを用いて可読性を向上)
大変読みやすくなった。
今回の場合は大きな変化はないが、breakするほうが、
スコープや変数の寿命が短く、メモリや処理時間の短縮にもなるようだ。
