
# web2


* 根据代码提示，写出反向代码
``` 
<?php

$_o = base64_decode(strrev(str_rot13("a1zLbgQsCESEIqRLwuQAyMwLyq2L5VwBxqGA3RQAyumZ0tmMvSGM2ZwB4tws")));

for($_0=0;$_0<strlen($_o);$_0++){
        $_c=substr($_o,$_0,1);
        $__=ord($_c)-1;
        $_c=chr($__);
        $_=$_.$_c;   
}
echo strrev($_);
```

