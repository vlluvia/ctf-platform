
# 签到题

* base64 解密

* 栅栏密码解密

* caesar密码解密
``` 

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

# e = 'ggQ@gQ1fqh0ohtjpt_sw{gfhgs#}'
# rail_fence_cipher(e)

caesar_cipher('ggqht{ggQht_gsQ10jsf#@fopwh}')
```



