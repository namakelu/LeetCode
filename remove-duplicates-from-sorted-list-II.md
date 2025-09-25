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

#2回目

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_node = ListNode(0)
        dummy_node.next = head
        before_node = dummy_node
        current_node = head
        while current_node:
            if current_node.next and current_node.val == current_node.next.val:
                duplicated_val = current_node.val
                while current_node and current_node.val == duplicated_val:
                    before_node.next = current_node.next
                    current_node = current_node.next
            else:
                before_node = current_node
                current_node = current_node.next
        return dummy_node.next
```

感想
before_node.next = current_node.nextについて、whileの中で都度設定してしまった。
こちらのほうが直感的にノードの移り変わりが理解しやすいが、計算量やメモリの使用量はおおいに増える。
何も見ずに書くと、while文の条件にis not Noneの条件を書き忘れる。
whileの中身を見て、前提条件がなにか逐一考えるクセをつけたい。

#3回目
```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_node = ListNode(0)
        dummy_node.next = head
        before_node = dummy_node
        current_node = head
        while current_node is not None and current_node.next is not None:
            if current_node.val == current_node.next.val:
                duplicated_val = current_node.val
                while current_node is not None and current_node.val == duplicated_val:
                        current_node = current_node.next
                before_node.next = current_node
            else:
                before_node = current_node
                current_node = current_node.next
        return dummy_node.next
```
大まかな流れは記憶していたが、[]のケースや[1,1]といった例示されていないケースが抜けており、後から何回か直すこととなった。まだあイメージをしっかりつかめていないかも。
 while current_node is not None and current_node.val == duplicated_val:
 この一行がさらっと出せるようになりたい。



        