
# miscmisc

* winhex 打开文件 发现有隐藏文件， 改成rar进行解压

* 解压后有一个加密的压缩包（chayidian.rar），和一张图片（chayidian.jpg）

* winhex 打开 chayidian.jpg 发现也有隐藏文件，改成rar， 解压

* 解压后有一个文本，用winrar打开发现这个文本的CRC与chayidian.rar中的CRC一致。明显是明文攻击

* winrar 压缩flag.txt

* ARCHPR进行明文攻击

* StegSolve打开图片 LSB + BGR + RED 0 + Green 0 + Blue 0
> 得到pass：z^ea

* winhex 打开 world.doc 有特别字符
``` 
 Z d f a w 1 2 3 4 
 3 d a e g h a l z 
 2 a e a q r q f a 
 W e a s a 6 5 f a 
 E z a f a s f a s f 3 
 S a d e r a 8 5 f a 
 D a a s z f f a s f z 
 A s d f a f s f a f f 
 S a d 5 4 6 5 6 a 8 
```
 
 * 实在想不到 看了wp
``` 
出题人真不要脸，最后来了一个脑筋急转弯，谁会想到最后的密码是 pass内容+world里每行字符串的最后一个字符，
就是密码 ：z^ea4zaa3azf8 
```


