■一回目
特筆すべきこともなく、素直に頭から解くことができた。
模範解答を確認したところ、list型で宣言せずに最初からset型で宣言する形で良かった。
set型でadd()を使うと、uniqueではない場合エラー等も起きずに無視される仕様だった。
それを踏まえていれば上記のような書き方が思いついたかもしれない。

```py

class Solution:
    def numUniqueEmails(self, emails: List[str]) -> int:
        modified_addresses = []

        for email in emails:
            obj_local,obj_domain = email.split('@')
            obj_local = obj_local.replace('.','')
            obj_local = obj_local.split('+')[0]
            obj = obj_local + '@' +obj_domain
            modified_addresses.append(obj)

        return len(set(modified_addresses))
                     
```
