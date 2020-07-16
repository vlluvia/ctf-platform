
# halo

* 题目有问题
> flag{jdr78672Q82jhQ62jaLL3}

* base64解密，然后异或
``` 
import string

from base64 import *

b = b64decode("aWdxNDs1NDFSOzFpa1I1MWliT08w")
data = list(b)

for k in range(0, 200):
    key = ""
    for i in range(len(data)):
        key += chr(data[i] ^ k)
    print(key)
```
