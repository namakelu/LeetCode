```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast_pointer = head
        slow_pointer = head

        while(fast_pointer and fast_pointer.next):
            fast_pointer = fast_pointer.next.next
            slow_pointer = slow_pointer.next

            if(fast_pointer == slow_pointer):
                return True
        
        return False

# Example 1:

# Input: head = [3,2,0,-4], pos = 1
# Output: true
# Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
# Example 2:

# Input: head = [1,2], pos = 0
# Output: true
# Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
# Example 3:

# Input: head = [1], pos = -1
# Output: false
# Explanation: There is no cycle in the linked list.
 
# Input: head = [], pos = -1
# Output: false

# Constraints:

# The number of the nodes in the list is in the range [0, 104].
# -105 <= Node.val <= 105
# pos is -1 or a valid index in the linked-list.
 
# Follow up: Can you solve it using O(1) (i.e. constant) memory?

```

感想
全く歯が立たず。解説を読みながら何度もテストを回してようやく完成。
基本的な空要素や境界値などのケースは事前に想定したい。
