# 1回目

```py
class Solution:
    def kSmallestPairs(self, nums1: List[int], nums2: List[int], k: int) -> List[List[int]]:
        if not nums1 or not nums2:
            return []
        
        matches = []
        heapq.heapify(matches)
        res = []

        for idx1 in range(min(k,len(nums1))):
            heapq.heappush(matches, (nums1[idx1] + nums2[0], idx1, 0)) 
        
        while matches and len(res) < k:
            val,idx1,idx2 = heapq.heappop(matches)
            res.append([nums1[idx1], nums2[idx2]])

            if idx2 + 1 < len(nums2):
                heapq.heappush(matches,(nums1[idx1] + nums2[idx2+1],idx1, idx2+1))
        return res

```
他人の回答を見て写経
for文の二重入れ子で回して組み合わせを作成するのかと考えたが、
前回のTop K Frequent Elementsで学んだように、
回答の必要数以上の組み合わせを作成する必要がないと考えるところまではできた。

どのように最小の組み合わせを判定するかで行き詰ってしまった。
(0,0)(0,1)(1,0)の三つの組み合わせを比較して回答となるリストに追加する案を考えたが、
[1,1,1,2],[1,1,1,2,3,4],k=8　のようなパターンを考えて断念した。

他人の回答をみて、valueとインデックスをまとめてheapqに渡すやり方が発想の中になかったと感じた。
たしかに、valueをキーとして与えてしまえば最小値の比較判定が不要だったなと
ヒントはあったのに思いつかなかった点が非常に悔しかった。