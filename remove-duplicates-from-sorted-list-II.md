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
        before_pointer = dummy_node
        current_pointer = head
        while current_pointer:
            if current_pointer.next and current_pointer.val == current_pointer.next.val:
                duplicated_val = current_pointer.val
                while current_pointer and current_pointer.val == duplicated_val:
                    current_pointer = current_pointer.next
                before_pointer.next = current_pointer
            else:
                before_pointer = current_pointer
                current_pointer = current_pointer.next
        return dummy_node.next

        
```

感想
現在、一つ前、一つ後、の三要素の比較が必要だと考えたが、うまくコードに落とすことができなかった。
AIの助けをもらいながらコードに落とし込んだ。
二重ループとなっているため計算量が多いかと思っていたが、
比較対象が少ないためそれほど多くならないらしい。

また、要素をduplicated_listのような形でリストにして比較する方法も考えたが、
先頭と終端の処理が複雑になり、計算量も多くなりそうだったため断念した。