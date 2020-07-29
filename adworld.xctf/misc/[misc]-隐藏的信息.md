

# 隐藏的信息

* 八进制码 转成十进制，然后变为ASCII字符
``` 
import re

with open('message.txt', 'r') as f1:
    s1 = f1.read()
    s1 = re.split(' ',s1)
    for i in s1[0:-1]:
        print(chr(int(i,8)),end='')
    f1.close()
```
