

# insanity

* ida（32位）打开文件，f5

* 发现程序很简单，推测puts((&strs)[v4 % 0xA]);就是输出flag

* 查看strs就得到flag
> 9447{This_is_a_flag}
