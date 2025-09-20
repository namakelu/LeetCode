```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

# Step1
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited_node = []
        current_pointer = head

        while current_pointer is not None:
            if current_pointer in visited_node:
                return True
            else:
                visited_node.append(current_pointer)
                current_pointer = current_pointer.next
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
レビューいただいた内容を反映した。（setを使用した解法。）
解答例はnanaeさんの下記のプルリクエストを参照した。
https://github.com/nanae772/leetcode-arai60/blob/141-linked-list-cycle/141-linked-list-cycle/step1.py

ノードの量が増えると、visited_node[]の量が増え、メモリの使用量が増えるという問題はあるが、
こちらの方が、素直な解き方で汎用性が高いと感じた。
フロイドのうさぎとかめのアルゴリズムは科学手品のように、面白いがあくまで導入のようなものらしい。

#step2

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        current_pointer = head
        visited_pointer_set = set()
        while current_pointer is not None:
            if current_pointer in visited_pointer_set:
                return True
            else:
                visited_pointer_set.add(current_pointer)
                current_pointer = current_pointer.next
        return False
```

感想
レビューいただいた内容を修正。
メモリの使用量はList型を使用したため大きく増加していたらしい。
Listは順序、Setは集合という認識。探索方法も線形探索とハッシュ探索で異なる。
違いを理解してちゃんと使い分けができるようになりたい。

Set型
https://docs.python.org/ja/3/library/stdtypes.html#set

List型
https://docs.python.org/ja/3/library/stdtypes.html#list
