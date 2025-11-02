# 1 回目

```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        frequecy = {}
        for n in nums:
            frequency[n] = frequency.get(n,0) + 1

        heap = []
        for num, count in freq.items():
            heapq.push(heap, (count, num))
            if len(heap) > k:
                heapq.heappop(heap)

        return [num for count, num in heap]

```
感想
辞書型で頻度を管理する箇所を連想配列で管理するアイデアまでは思いついたが、
挫折して他人の回答を見て写経を行った。

if len(heap) > k:　の箇所で処理を止めてしまう発想はなかった。
自身の傾向として、一度作りきる、やりきるという発想に偏りがちだと感じた。
