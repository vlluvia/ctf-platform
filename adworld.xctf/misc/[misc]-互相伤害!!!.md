
# 互相伤害!!!

* winhex 打开文件发现是数据流文件

* wireshark 打开文件， 导出对象/http , 将图片导出来

* winhex 打开图片文件， 发现还有隐藏文件，解压之后得二维码

* 扫描二维码, 只有70bf85eda6b86ee92a5f437f7d83b7e5.jpg 不一样
> 扔下内衣真有一线生机？？？？
  交出内裤才有活路！！！！

* 解压 70bf85eda6b86ee92a5f437f7d83b7e5.jpg 得到一个加密的rar

* 查看图片 4356f2b426ad8355c99e9388a3189c89.jpg. 有aes，ctf 还有二维码，

* 扫描二维码发现有加密数据
> U2FsdGVkX1+VpmdLwwhbyNU80MDlK+8t61sewce2qCVztitDMKpQ4fUl5nsAZOI7
  bE9uL8lW/KLfbs33aC1XXw==

* aes加密， CTF 为密码
> http://www.jsons.cn/aesencrypt/  
> 解密后: 668b13e0b0fc0944daf4c223b9831e49

* 用密码打开压缩包，里面有一张二维码，二维码中间还有二维码，直接扫描，得到flag

