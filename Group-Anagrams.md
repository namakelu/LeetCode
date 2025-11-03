#1回目

```py
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:    
        ans = defaultdict(list)

        for s in strs:
            key = "".join(sorted(s))
            ans[key].append(s)
        
        return list(ans.values())
```
strsから要素を取り出して、アナグラムにヒットするものをwhileで取り出す方法を考えたが
時間計算量がn^2以上になりそうなのであきらめた。（O(n² * k log k)らしい）
結局回答をみて写経した。
defaultdict()は場合分けで回避できるので、できれば下記の回答を使っていきたいと思う。
key = "".join(sorted(s))この書き方は便利なので覚えておきたい。

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:    
        ans = {}

        for s in strs:
            key = "".join(sorted(s))
            if key not in ans:       # もしまだキーがなければ初期化
                ans[key] = []
            ans[key].append(s)       # アナグラムグループに追加
        
        return list(ans.values())