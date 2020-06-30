
# warmup

* 发现 open_forum.png 与 压缩包内文件一致，明文攻击
``` 
注：需要解密的压缩包zip加密格式和open_forum.zip 格式一致
winrar压缩open_forum.png 到open_forum.zip

Archive 进行明文攻击
注：有的Archive的版本有问题，会一直尝试，其实已经破解出来，直接强行停止， 会弹出压缩文件
```

* 解压文件，有两张一样的png，推测盲水印
``` 
盲水印 推荐 python2
```

