


# 2-1

* 知识积累
``` 
先详细解释一下png的文件头：
- （固定）八个字节89 50 4E 47 0D 0A 1A 0A为png的文件头
- （固定）四个字节00 00 00 0D（即为十进制的13）代表数据块的长度为13
- （固定）四个字节49 48 44 52（即为ASCII码的IHDR）是文件头数据块的标示（IDCH）
- （可变）13位数据块（IHDR)
    - 前四个字节代表该图片的宽
    - 后四个字节代表该图片的高
    - 后五个字节依次为：
    Bit depth、ColorType、Compression method、Filter method、Interlace method
- （可变）剩余四字节为该png的CRC检验码，由从IDCH到IHDR的十七位字节进行crc计算得到。
也就是说我们可以通过爆破来得到高度和宽度
```

* winhex打开后发现文件头不对，然后修改过来，但是仍然打不开

* IHDR和crc之间的错误，应该是宽度的问题，我们可以用图片数据进行爆破来得到宽度
``` 
import struct
import binascii
import os
 
m = open("misc4.png","rb").read()
for i in range(1024):
    # 宽度爆破
    c = m[12:16] + struct.pack('>i', i) + m[20:29]
    # 高度爆破
    # c = m[12:20] + struct.pack('>i', i) + m[24:29]
    crc = binascii.crc32(c) & 0xffffffff
    if crc == 0x932f8a6b:
        print(i)
```

