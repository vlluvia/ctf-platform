
#Shrek

``` 
nmap -sS -sV -oA nmap/shrek 10.10.10.47
```
vsftpd
``` 
searchsploit vsftpd 
```
> /upload.php
> /uploads -> /secret_area51 -> 音频文件
``` 
gobuster -u http://10.10.10.47 -w /usr/share/wordlists/dirbusters/directory.txt
```

解密音频文件,得到donkey : donk3y1337!  
ftp连接，下载文件， 放到quipquip网站解密  
base64解密
``` 
for i in `ls *.txt`; do echo $i; do base64 -d $i > $i.b64; done
```
打开文件，发现有一段文字前后空格，提取出单独解密
41a547...txt  
ebb514...txt
``` 
pip install seccure
python
> import seccure
seccure.decrypt(ct, b'')
```
得到ssh密码，登录即可
``` 
ssh sec@10.10.10.10.47

sudo -u farquad /usr/bin/vi
```




