

# picture3

* winhex打开文件发现有隐藏文件

* foremost 分解文件

* 分解出一个压缩包，解压后得到txt，打开txt，有被base64解密的密文

* 正常base64解密，没有flag， 推测是base64隐写
> https://www.tr0y.wang/2017/06/14/Base64steg/
```` 
# -*- coding: cp936 -*-
import base64
b64chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/'
with open('C:\\Users\\Administrator\\Desktop\\s\\stego.txt', 'rb') as f:
    bin_str = ''
    for line in f.readlines():
        # print()
        stegb64 = ''.join(str(line,'utf-8').split())
        de2 = base64.b64decode(stegb64)
        rowb64 =  ''.join(str(base64.b64encode(de2),'utf-8').split())
        offset = abs(b64chars.index(stegb64.replace('=','')[-1])-b64chars.index(rowb64.replace('=','')[-1]))
        equalnum = stegb64.count('=') #no equalnum no offset
        if equalnum:
            bin_str += bin(offset)[2:].zfill(equalnum * 2)
        print(''.join([chr(int(bin_str[i:i + 8], 2)) for i in range(0, len(bin_str), 8)])) #8 位一组

````
* 得到flag
> Ba5e_64OFive