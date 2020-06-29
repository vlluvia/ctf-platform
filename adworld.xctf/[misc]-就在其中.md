
# 就在其中

* 分析数据包，358数据帧有private key

* 尝试foremost 分离文件

* 有压缩包 解压，之后有加密的txt

* ssl 破解txt
``` 
openssl rsautl -decrypt -in key.txt -inkey psa.key -out flag.txt
```

