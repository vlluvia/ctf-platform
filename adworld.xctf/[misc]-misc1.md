
# misc1

* 16进制转换成10进制的数余128再转换成16进制数最后使用转换工具，将16进制转换成字符串
``` 
qu = '你的字符串'
hex_new = ''
for i in range(0,len(qu),2):
    hex_ = qu[i:i+2]
    d_ = int('0x'+ hex_, 16)
    d_surplus = d_%128
    temp = hex(d_surplus)[2:4]
    hex_new+=temp
print(str(hex_new))

```
