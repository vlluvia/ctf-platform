
# picture

* 分离图片文件 97E4和97E4.zlib
``` 
  bin­walk a.png -e
``` 

* 打开97E4，base64解压成文件，将文件头KP改为PK

* 解压修改后的rar文件，得到注释
``` 
  [Python 2.7]
>>> ▆▆▆

Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    ▆▆▆
ZeroDivisionError: ▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆▆ <- password ;)
>>> 
``` 
* ZeroDivisionError的错误即密码
``` 
integer division or modulo by zero
```
* 解压后得到文件
```
begin 644 key.txt
G0TE30TY[,C,X.$%&,C@Y,T5".#5%0C%"-#,Y04)&1C8Q-S,Q.49]
`
end
```
* Uuencode解码
``` 
CISCN{2388AF2893EB85EB1B439ABFF617319F} 
```
