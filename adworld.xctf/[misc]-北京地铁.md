
# 北京地铁
* Stegsolve.jar 打开图片,数据分析
> MSB RGB    
> RED 0    
> Green 0  
> Blue 0

* 获得一串AES ECB 加密的文件

* 查看图片，魏公村颜色不对，密钥为weigongcun
``` 
from Crypto.Cipher import AES
 
key='weigongcun'
cryptor = AES.new(key+(16-len(key))*'\x00', AES.MODE_ECB)
text = cryptor.decrypt('7SsQWmZ524i/yVWoMeAIJA=='.decode('base64'))
print text
```
