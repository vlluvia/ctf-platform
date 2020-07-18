
* 题目
``` 
I try to secure my pages with .htaccess.
Am I doing it right?

To prove me wrong, please access protected/protected.php.
```

* 解析
``` 

AuthUserFile .htpasswd
AuthGroupFile /dev/null
AuthName "Authorization Required for the Limited Access Challenge"
AuthType Basic
<Limit GET>
require valid-user
</Limit>
 
```

* 解题
> 用POST访问
