
# Disk

* 前言

> ADS: NTFS使用Master File Table (MFT) 来管理文件。windows系统中的每个文件都对应一个MFT记录。而每一个MFT记录由若干个属性(attribute)组成，用来描述该文件的具体信息。比如 $FILE_NAME 属性描述了该文件的文件名和创建修改访问时间，而$DATA属性包含了该文件的具体内容。

> https://www.freebuf.com/articles/73270.html

* 解压压缩包， 发现4个 txt的ads不一致， 提取出, 得到一串二进制

* 二进制转字符串
