
# 一回目 
```py

class KthLargest:

    def __init__(self, k: int, nums: List[int]):
        self.k = k
        self.nums = nums
        heapq.heapify(self.nums)
        while len(self.nums) > k:
            heapq.heappop(self.nums)
        
    def add(self, val: int) -> int:
        heapq.heappush(self.nums, val)
        if len(self.nums) > self.k:
            heapq.heappop(self.nums)
        return self.nums[0]

# Your KthLargest object will be instantiated and called as such:
# obj = KthLargest(k, nums)
# param_1 = obj.add(val)

# Your KthLargest object will be instantiated and called as such:
# obj = KthLargest(k, nums)
# param_1 = obj.add(val)

```
感想:
下記のような形で素直に力押して回答を作成してタイムアウトした。
リストのソートに都度、O(n log n)の計算量がかかるので筋悪ということらしい。
その結果、他人の回答を見て回答を作成した。

ヒープソート、キューといった概念は知っていたが、
heapqというクラスを知らなかったので、勉強になった。

問題を読んで頭に浮かんだ回答プランについて、
Listに破壊的変更を加えていくという発想はあったが、
常に最小値を返すようにするという発想はなかった。
こういう方法が選択肢として浮かぶ状態を目指したい。

```py
class KthLargest:

    def __init__(self, k: int, nums: List[int]):
        self.index = k - 1
        self.nums = nums
        
    def add(self, val: int) -> int:
        self.nums.append(val) 
        sorted_list =sorted(self.nums, reverse=True)　# ← 全体をソート (O(n log n))
        return sorted_list[self.index]
        
```