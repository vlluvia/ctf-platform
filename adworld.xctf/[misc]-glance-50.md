

# glance-50

> 代码不会，网上借鉴

* 分离gif
``` 
#分离gif.py
from PIL import Image

savepath = "F:\ctf文件\\D-R0s1\\" #保存路径

im = Image.open('F:\ctf文件\\1.gif')   #从文件加载图像
try:
    im.save(savepath+'{:d}.png'.format(im.tell())) #读取每一帧
    while True:
        im.seek(im.tell()+1) #在不同帧之间移动
        im.save(savepath+'{:d}.png'.format(im.tell()))  #保存文件
except:
    pass
```

* 图像拼接
``` 
#拼接图像.py
from PIL import Image
path = "F:\\ctf文件\\D-R0s1\\"
save_path = 'F:\\ctf文件\\'

im = Image.new('RGBA',(2*201,600)) #创建新照片

    imagefile = [] #存储所有的图像的名称
    width = 0
    for i in range(0,201):
        imagefile.append(Image.open(path+str(i)+'.png')) #遍历，将图像名称存入imagfile

for image in imagefile:
    im.paste(image,(width,0,2+width,600)) #将图片张贴到另一张图片上
    width = width +2
im.save(save_path+'D-R0s1.png')
im.show()

```



