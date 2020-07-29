
# 双色块


* gif 按帧分解成 图片
``` 
# python
import PIL.Image as Image
import os


def gif_split(path):
    save_path = path[:-4]
    try:
        os.mkdir(save_path)
    except :
        pass

    img = Image.open(path)
    try:
        i = 0
        while True:
            print("正在拆解第{}帧...".format(i))
            img.seek(i)
            img.save('{}/'.format(save_path) + str(i) + '.png')
            i += 1
    except:
        pass
    return save_path, i


if __name__ == '__main__':
    path = 'out.gif'
    save_path, i = gif_split(path)
    print('拆解完成，共得到{}张图片。所属文件:{}'.format(i,save_path))

```

* 以紫色为1， 绿色为0
``` 
# python
"""
python3 code
"""

# !/usr/bin/env python
# -*- coding: utf-8 -*-
# @Author  : B1u3Buf4(https://www.cnblogs.com/xiao3c/)


from PIL import Image
import os

p = os.listdir('out/')
tmp = [0 for i in range(576)]
cur = -1
print(p)
for i in p:
    #print(i)
    im = Image.open('out/' + i)
    im = im.convert('RGBA')
    w, h = im.size
    cur = int(i.split('.')[0])
    # print(cur)
    # 返回一个用于读取和修改像素的像素访问对象
    st = im.load()
    flag = False
    for x in range(w):
        for y in range(h):
            if flag: break
            if st[x, y][1] > 250 and (st[x, y][0] < 10 and st[x, y][2] < 10):
                if flag == False:
                    flag = True
                    tmp[cur] = 0
                    continue
            if st[x, y][1] < 10 and (st[x, y][0] > 250 and st[x, y][2] > 250):
                if flag == False:
                    flag = True
                    tmp[cur] = 1
                    continue

print(tmp)

b = [tmp[i:i + 8] for i in range(0, len(tmp), 8)]
res = ""
for t in b:
    str1 = ''.join(str(i) for i in t)
    res += chr(int(str1, 2))
print(res)

```
* foremost 发现有隐藏文件，获得key

* DES 解密
> http://tool.chacuo.net/cryptdes


