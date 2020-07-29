
# Reverse-it

* 反转二进制文件
``` 
#python
filename1 = 'Reverseit.txt'
 filename2 = 'flag.txt'
 s = ''
 with open(filename1,'r') as fp:
     for line in fp:
         s += line.strip('\n')
     s = s[::-1].replace(' ','')
 with open(filename2,'w') as fp:
     fp.write(s)
 print('done')
```
