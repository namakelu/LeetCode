■１回目
```py
class Solution:
    def firstUniqChar(self, s: str) -> int:
        char_set = dict()
        char_list = list(s)
        for i,val in enumerate(char_list):
            if char_set.get(val) is None:
                char_set[val] = i

        minimum_i = 10**5
        for char in  char_set.keys():
            if char_list.count(char) == 1:
                if minimum_i > char_set[char]:
                    minimum_i = char_set[char]

        if minimum_i == 10**5:
            return -1
        else:
            return minimum_i
```
素直に頭から説いたらこうなった。回答はできたが遅い。
char * char_list.count() がO(n**2)となっているのが良くないそう。
同じ考え方で解き方を修正した。
```py
class Solution:
    def firstUniqChar(self, s: str) -> int:
        char_dict = {}

        for i, char in enumerate(s):
            if char in char_dict:
                char_dict[char][1] += 1
            else:
                char_dict[char] = [i, 1] 

        answer = float('inf')
        for index, count in char_dict.values():
            if count == 1:
                answer = min(answer, index)
 
        if answer == float('inf') :
            return -1
        else:
            return answer
```
collection型を使ったほうが早いらしいのだが、なんとなくimportを使うのを避けてしまう。
原理は一緒らしいのだが、どのような姿勢で臨むのがいいのだろうか。
        

■２回め
```py

class Solution:
    def firstUniqChar(self, s: str) -> int:
        count = {}

        for char in s:
            count[char] = count.get(char,0) + 1

        for i,char in enumerate(s):
            if count[char] == 1:
                return i

        return -1


```
番兵を使わない方法で書いた。こっちのほうが変数が少なくて読みやすい。
やっていることはほとんど同じなので、時間計算量も空間計算量も変わらない。
