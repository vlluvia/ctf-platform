

# Keyword

* [目标]
> lsb隐写，Nihilist 密码
* [环境]
> pyhton
* [工具]
> cloacked-pixel （https://github.com/livz/cloacked-pixel），python
* [分析过程]
> 一张图片，上 Stegsolve ，发现图片开头 lsb 里有些东西。  
  用 lsb 解密脚本 python lsb.py extract keyword.png out lovekfc  
  打开out后得到PVSF{vVckHejqBOVX9C1c13GFfkHJrjIQeMwf}  
  根据题目提示，尝试了一下，发现是 Nihilist 密码 。  

``` 
enc='PVSF{vVckHejqBOVX9C1c13GFfkHJrjIQeMwf}'
grid='LOVEKFC'+'ABDGHIJMNPQRSTUWXY' flag=''

for i in enc: if i in string.ascii_lowercase: index=grid.lower().index(i)
flag+=string.ascii_lowercase[index] continue if i in string.ascii_uppercase:
index=grid.upper().index(i) flag+=string.ascii_uppercase[index] continue
flag+=i print flag ``` \- 得到flag QCTF{cCgeLdnrIBCX9G1g13KFfeLNsnMRdOwf}
```
