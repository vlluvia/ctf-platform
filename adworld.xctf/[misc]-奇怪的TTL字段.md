
# 奇怪的TTL字段

* ttl.txt
> 发现ttl.txt中的ttl只有4个值63,127,191,255，写出他们的二进制表示后发现只有最高两位不同
  于是考虑做如下转换，发现写出来的16进制数开头是ffd8，应该是jpg
``` 

fp = open('ttl.txt','r')
a = fp.readlines()
p = []
for i in a:
    p.append(int(i[4:]))
s = ''
for i in p:
    if i == 63:
        a = '00'
    elif i == 127:
        a = '01'
    elif i == 191:
        a = '10'
    elif i == 255:
        a = '11'
    s += a
# print(s)

import binascii
flag = ''
for i in range(0,len(s),8):
    flag += chr(int(s[i:i+8],2))
flag = binascii.unhexlify(flag)
wp = open('res.jpg','wb')
wp.write(flag)
wp.close()
#00111111 63
#01111111 127
#10111111 191
#11111111 255
```

* foremost
> 写完之后发现只有二维码的一部分，应该是不止一张图，用foremost直接分开就好了，之后用ps拼在一块，扫描之后得到如下信息

``` 
key:AutomaticKey cipher:fftu{2028mb39927wn1f96o6e12z03j58002p}
```

* 在线网站解密
> https://www.wishingstarmoye.com/ctf/autokey





