
# 传感器1

* 曼彻斯特编码
>  在曼彻斯特编码中，每一位的中间有一跳变，位中间的跳变既作时钟信号，又作数据信号；从高到低跳变表示"1"，从低到高跳变表示"0"。还有一种是差分曼彻斯特编码，每位中间的跳变仅提供时钟定时，而用每位开始时有无跳变表示"0"或"1"，有跳变为"0"，无跳变为"1"。

* 十六进制转成二进制， 根据曼彻斯特准则，解密
``` 
#!/usr/bin/env python      
#coding:utf-8
 
import re 
 
#hex1 = 'AAAAA56A69AA55A95995A569AA95565556' # #  0x8893CA58
hex1 = 'AAAAA56A69AA556A965A5999596AA95656'
 
def bintohex(s1):
    s2 = ''
    s1 = re.findall('.{4}',s1)
    print ('每一个hex分隔:',s1)
    for i in s1:
        s2 += str(hex(int(i,2))).replace('0x','')
 
    print ('ID:',s2)
 
 
def diffmqst(s):
    s1 = ''
    s = re.findall('.{2}',s)
    cc = '01'
    for i in s:
        if i == cc:
            s1 += '0'
        else:
            s1 += '1'
        cc = i  # 差分加上cc = i
 
    print ('差分曼切斯特解码:',s1)
    bintohex(s1)
 
 
 
 
def mqst(s):  #只能算曼切斯特编码,无法算差分
    mdict = {'5': '00', '6': '01', '9': '10', 'A': '11'}
    a1 = ''.join(mdict[i] for i in s)
    a2 = ''.join(mdict[i][::-1] for i in s)
    print ('曼切斯特解码:   ',a1 )
    print ('曼切斯特解码2:  ',a2)
    bintohex(a1)
    bintohex(a2)
 
 
if __name__ == '__main__':
    bin1 = bin(int(hex1,16))[2:]
    diffmqst(bin1)
 
    mqst(hex1)
```
