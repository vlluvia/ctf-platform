
# picture2

* binwalk 查看、分解数据包
``` 
binwalk -e e4103617b4a6476fb7aa8f862f2ee400.png
```

* 查看一个文件，发现是base64加密数据
``` 
import base64

t = "S1ADBBQAAQAAADkwl0xs4x98WgAAAE4AAAAEAAAAY29kZePegfAPrkdnhMG2gb86/AHHpS0GMqCrR9s21bP43SqmesL+oQGo50ljz4zIctqxIsTHV25+1mTE7vFc9gl5IUif7f1/rHIpHql7nqKPb+2M6nRLuwhU8mb/w1BLAQI/ABQAAQAAADkwl0xs4x98WgAAAE4AAAAEACQAAAAAAAAAIAAAAAAAAABjb2RlCgAgAAAAAAABABgAAFvDg4Xa0wE8gAmth9rTATyACa2H2tMBUEsFBgAAAAABAAEAVgAAAHwAAADcAFtQeXRob24gMi43XQ0KPj4+IKh9qH2ofQ0KDQpUcmFjZWJhY2sgKG1vc3QgcmVjZW50IGNhbGwgbGFzdCk6DQogIEZpbGUgIjxweXNoZWxsIzA+IiwgbGluZSAxLCBpbiA8bW9kdWxlPg0KICAgIKh9qH2ofQ0KWmVyb0RpdmlzaW9uRXJyb3I6IKh9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofah9qH2ofSA8LSBwYXNzd29yZCA7KQ0KPj4+IAA="
a = base64.b64decode(t)
with open('a', "bw") as f:
    f.write(a)
    f.close()

```

* winhex查看文件的二进制，发现文件头有错KP 转成PK

* 打开压缩包还需要有密码,右侧已经提示密码信息
``` 
integer division or modulo by zero
```

* 解压之后，winhex打开文件，根据查找资料，发现是uuencode
> Linux 指令篇:编码压缩打包--uudecode
``` 
uudecode 输出名
```

* 查看输出文件，获得flag
> CISCN{2388AF2893EB85EB1B439ABFF617319F}
