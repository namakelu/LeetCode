■一回目
特筆すべきこともなく、素直に頭から解くことができた。

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
