#１回目
```py
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        nums1set = set(nums1)
        nums2set = set(nums2)
        answers = []
        if(len(nums1set)<len(nums2set)):
            while nums1set:
                popped_item = nums1set.pop()
                if(popped_item in nums2set and  popped_item not in answers):
                    answers.append(popped_item)
        else:
            while nums2set:
                popped_item = nums2set.pop()
                if(popped_item in nums1set  and popped_item not in answers):
                    answers.append(popped_item)
        return answers

```
素直に頭から解いていくことができた。回答を見ずに正当。
要素数の差によって計算時間量が増えないように、
if(len(nums1set)<len(nums2set)):
のif文をかませるように工夫した。
setを使っているので、popped_item not in answers の条件は不要だった。
O(min(n,m))の時間計算量。（内部的にはsetを使っているので違うけど。）

他の回答を見ると下記のようだった。数字の表出回数は回答に関係ないので
自身で考えたようにset型を使用してもいいのではないかと考えている。
ただし、時間計算量は O(n + m)と優れている。

class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        mp = {}
        for num in nums1:
            mp[num] = mp.get(num, 0) + 1
        
        result = []
        for num in nums2:
            if num in mp:
                result.append(num)
                del mp[num]
        
        return result

極限に圧縮すると下記の一行で完結するらしい。
可読性も高いので、個人的にはこれが一押し。

return list(set(nums1) & set(nums2))
