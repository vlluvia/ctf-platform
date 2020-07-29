
# Miscellaneous-300

* 压缩包密码是包内文件名
``` 
import zipfile
import re
zipname = "D:\\001\\ziptest\\"+"misc.zip"
while True:
    if zipname != "D:\\001\\ziptest\\73168.zip":
        ts1 = zipfile.ZipFile(zipname)
        #print ts1.namelist()[0]
        res = re.search('[0-9]*',ts1.namelist()[0])
        print res.group()
        passwd = res.group()
        ts1.extractall("D:\\001\\ziptest",pwd=passwd)
        zipname = "D:\\001\\ziptest\\"+ts1.namelist()[0]
    else:
        print "find"

```

* 最后一个压缩包爆破就行

* 文件拖入Audacity中查看频谱图


