
# 5-1

* 简介
>  xortool        XOR 分析工具

* xortool 操作文件
> xortool cipher -l 13 -c 20

* 用得到的key，对文件异或
``` 
key = 'GoodLuckToYou'
flag = ''
with open('cipher') as f:
    con = f.read()
    for i in range(len(con)):
        flag += chr(ord(con[i]) ^ ord(key[i%13]))
f = open('flag.txt', 'w')
f.write(flag)
f.close()
```
