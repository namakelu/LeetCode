Step1
```py
class Solution:
    def isValid(self, s: str) -> bool:
        brackets = {")":"(","}":"{","]":"["}
        stack = []
        for char in s :
            if char in brackets:
                if stack and brackets[char] == stack[-1]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(char)
        return len(stack) == 0
```
感想
最初はキューを作って先頭と後ろから値を撮ってきて比較しようと考えたが、"｛,（,）,[,],｝"のようなパターンがある場合に
比較対象が増えるなと考え断念。他人の解答をみて解答を作成した。
最初はうまく行かないのではないかと直感的に考えていたが、順を追うと様々なケースに対応できており驚いた。
必ず先に開きカッコが現れるため、開きカッコを蓄えたstackと、閉じカッコのcharを比較するアイデアがすばらしい。
後ろの閉じカッコをキーとの辞書型の連想配列を使うアイデアも思いつかなかった。順序も関係ないので素晴らしい方法だと感じた。

