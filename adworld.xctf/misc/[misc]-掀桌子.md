
# 掀桌子

* 字符串分为2个一组，转成16进制的数，模128（因为ASCII码的可显示字符最大为128）
``` python
# python
m = "c8e9aca0c6f2e5f3e8c4efe7a1a0d4e8e5a0e6ece1e7a0e9f3baa0e8eafae3f9e4eafae2eae4e3eaebfaebe3f5e7e9f3e4e3e8eaf9eaf3e2e4e6f2"
num=""
for i in range(0,len(m),2):
    hex = m[i:i+2]
    num += chr(int(hex,16)-128)  #此处因为ascii只用了7位二进制,因此需对num减2的7次方即128
print(num) 
```

