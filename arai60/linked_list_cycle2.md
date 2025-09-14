````py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast_pointer = head
        slow_pointer = head
        if (head is None):
            return None

        while(fast_pointer and fast_pointer.next):
            fast_pointer = fast_pointer.next.next
            slow_pointer = slow_pointer.next

            if(fast_pointer == slow_pointer):
                lists = []
                node = head
                while(True) :
                    lists.append(node)
                    if (len(lists) != len(set(lists))):
                        return node
                    node = node.next
        return None

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

````

感想
答えを見ずに自力で考えてみたが処理速度が遅すぎる。
テストケースの空集合を想定して早期リターンできたのはよい。
解答をみて、素直に力技で解くのはよくないなと反省しました。
