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

step2
```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(
        self, l1: Optional[ListNode], l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        dummy_node = ListNode(-1)
        node = dummy_node
        carry_up_digit = 0
        while l1 is not None or l2 is not None or carry_up_digit != 0:
            total = 0
            if l1 is not None:
                l1_digit = l1.val
                l1 = l1.next
                total += l1_digit
            if l2 is not None:
                l2_digit = l2.val
                l2 = l2.next
                total += l2_digit
            total += carry_up_digit
            sum_digit = total % 10
            carry_up_digit = total // 10
            node.next = ListNode(sum_digit,None)
            node = node.next
        return dummy_node.next
```
感想
繰り上がり桁数含めて、計算方法は素直に思いついた。
if文内で都度totalを宣言したが、これは無駄な計算時間を使う形になっている。
step1のようにwhile内でlq_digitの値を0と宣言しておけば、l1,l2の有無を確認せずに足し上げることができてうまいやり方だなと感じた。
計算時間も段違いに早くなる。
ノードの宣言方法を忘れていて困った。
