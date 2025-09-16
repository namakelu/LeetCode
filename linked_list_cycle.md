```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow_pointer = head
        fast_pointer = head
        while fast_pointer is not None and fast_pointer.next is not None:
            slow_pointer = slow_pointer.next
            fast_pointer = fast_pointer.next.next
            if slow_pointer is fast_pointer:
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
レビューいただいた内容を反映した。（()の不使用、is Noneの使用。）
解答例はAraiさんの動画とnanaeさんの下記のプルリクエストを参照した。
youtube.com/watch?v=kOhQ5bfpq2I&feature=youtu.be
https://github.com/nanae772/leetcode-arai60/pull/2/files

他の方の解答もいろいろ見てみたが、色々な表記があって大変参考になった。
コメントの指摘内容から計算量など見えている角度が全然違うなと思った。
こういった点も学ばなければならない。
