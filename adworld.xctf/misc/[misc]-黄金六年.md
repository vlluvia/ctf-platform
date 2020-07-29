
# 黄金六年

* winhex 查看视频文件， 最后有加密密码
``` 
UmFyIRoHAQAzkrXlCgEFBgAFAQGAgADh7ek5VQIDPLAABKEAIEvsUpGAAwAIZmxhZy50eHQwAQADDx43HyOdLMGWfCE9WEsBZprAJQoBSVlWkJNS9TP5du2kyJ275JzsNo29BnSZCgMC3h+UFV9p1QEfJkBPPR6MrYwXmsMCMz67DN/k5u1NYw9ga53a83/B/t2G9FkG/IITuR+9gIvr/LEdd1ZRAwUEAA==
```

* 网页尝试解密base64， 发现是rar二进制文件 

* base64 解密之后，存放到rar
``` 

import base64

s = "UmFyIRoHAQAzkrXlCgEFBgAFAQGAgADh7ek5VQIDPLAABKEAIEvsUpGAAwAIZmxhZy50eHQwAQADDx43HyOdLMGWfCE9WEsBZprAJQoBSVlWkJNS9TP5du2kyJ275JzsNo29BnSZCgMC3h+UFV9p1QEfJkBPPR6MrYwXmsMCMz67DN/k5u1NYw9ga53a83/B/t2G9FkG/IITuR+9gIvr/LEdd1ZRAwUEAA=="
res = base64.b64decode(s)
fo = open('text.rar', "wb")
fo.write(res)
fo.close()
print(res)

```

* 打开压缩包发现有密码， 用pr打开视频文件，逐帧查看，发现有四张图片有二维码
1. c++
2. 白帽子讲Web安全
3. 逆向工程核心原理
4. 活着

> iwantplayctf

* 压缩包用密码解密




