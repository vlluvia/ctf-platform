
# 再见李华

* 分析题目
> 假如你是李华（LiHua)，收到乔帮主一封密信，没有任何特殊字符，请输入密码，不少于1000个字。同学，记得署名哦～
```
不少于1000个字， 1000当成二进制的话就是8
记得署名哦， 就是最后加上LiHua的字符串
分析密码基本格式: xxxxLiHua
```


* 解压之后获得一张图片，里面有不完整的md5

* 正经思路
> 爆破xxxxLiHua
``` 
# !python3
# coding:utf8

from hashlib import md5
import string

dic = string.printable

half_md5 = "1a4fb3fb5ee12307"

str1 = ""
for i1 in dic:
    for i2 in dic:
        for i3 in dic:
            for i4 in dic:
                str1 = i1 + i2 + i3 + i4 + "LiHua"
                str1_md5 = md5(str1).hexdigest()
                if half_md5 in str1_md5:
                    print(str1)
                    exit(0)

print("Done")
```

* 邪道
> ARCHPR 掩码爆破
