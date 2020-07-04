
# 我们的秘密是绿色的

* 第一步看别人的wp， 得知有OurSecret工具， 根据文件提示密码为图片日期的绿色部分

* 提取出 压缩包， 根据提示，生日有8位, 直接爆破
> 你知道coffee的生日是多少么~~~

* 里面还有压缩包，但是readme.txt 和 压缩包里的readme.txt，明文攻击

* 得到txt文件，根据密文推测是栅栏密码, 然后是凯撒密码
``` 
#!/usr/bin/env python
# -*- coding: gbk -*-
# -*- coding: utf_8 -*-
# Author: 蔚蓝行
# http://www.cnblogs.com/duanv

def  rail_fence_cipher(e):

    elen = len(e)
    field = []
    for i in range(2, elen):
        if (elen % i == 0):
            field.append(i)

    for f in field:
        b = int(elen / f)
        result = {x: '' for x in range(b)}
        for i in range(elen):
            a = i % b
            result.update({a: result[a] + e[i]})
        d = ''
        for i in range(b):
            d = d + result[i]
        print('分为\t' + str(f) + '\t' + '栏时，解密结果为：  ' + d)

def caesar_cipher(str):
    # 密钥(平移位数)
    elen = len(str)
    for my in range(elen):
        for i in str:
            mw = ord(i)
            if (64 < mw < 91):  # 大写字母
                jm = mw + my
                if jm > 90:
                    jm = (mw - 26) + my
                    print(chr(jm), end='')
                else:
                    print(chr(jm), end='')
            elif (96 < mw < 123):  # 小写字母
                jm = mw + my
                if jm > 122:
                    jm = (mw - 26) + my
                    print(chr(jm), end='')
                else:
                    print(chr(jm), end='')
            else:  # 数字和特殊字符不做修改
                jm = mw + 0
                print(chr(jm), end='')
        print(" ")

e = 'qddpqwnpcplen%prqwn_{_zz*d@gq}'
rail_fence_cipher(e)

caesar_cipher('qwlr{ddneq_@dpnwzgpc%nzqqpp_*}')

```




