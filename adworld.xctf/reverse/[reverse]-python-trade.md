

# python-trade


* 得到pyc文件，到在线反编译网站反编译
> http://tools.bugscaner.com/decompyle/
``` 
import base64

def encode(message):
    s = ''
    for i in message:
        x = ord(i) ^ 32
        x = x + 16
        s += chr(x)
    
    return base64.b64encode(s)

correct = 'XlNkVmtUI1MgXWBZXCFeKY+AaXNt'
flag = ''
print 'Input flag:'
flag = raw_input()
if encode(flag) == correct:
    print 'correct'
else:
    print 'wrong'
```

* 读源码可知
``` 
import base64
s='XlNkVmtUI1MgXWBZXCFeKY+AaXNt'
str=base64.b64decode(s)
print(str)


def decode(message):
	s = ''
	for i in message:
		x = ord(i) - 16
		x = x ^ 32
		s += chr(x)
	return s

print(decode(str))

```

* 得到flag
> nctf{d3c0mpil1n9_PyC}
