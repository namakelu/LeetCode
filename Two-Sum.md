#1回目

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        num_map = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in num_map:
                return [num_map[complement], i]
            num_map[num] = i

```
leetCodeの模範解答を見て写経。
辞書型を使うアイデアは全く浮かばなかった。
問に出ていた例の[3,3]が解けずに諦めてしまった。
回答を出すために何を覚えておくことが必要なのか、
そういった問題の分解の感覚を磨きたい。

#2回目

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}
        for i in range(len(nums)):
            pair = target - nums[i]
            if pair in seen:
                return [seen[pair],i]
            seen[nums[i]] = i
```
おおよそ見ずにかくことができた。
辞書型に関する苦手感覚が少しましになったと感じた。
そういえば、なぜこの問題がハッシュマップに分類されているのか意識していなかったが、
Pythonの辞書は、ハッシュテーブルを使って実装されているらしい。
キーバリュー型としか思っていなかったが、確かに、ハッシュ化しているなら速度が上がりそうだ。
衝突が起きても線形探索的な方法（オープンアドレッシング）で、解決できるらしい。