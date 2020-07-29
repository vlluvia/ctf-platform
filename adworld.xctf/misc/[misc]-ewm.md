
# ewm

* 拼接二维码
``` 
#-*- coding:utf-8 -*-
import PIL.Image as Image
import os
 
IMAGES_PATH = 'D:\\Desktop\\1\\0c0b0a79-1c40-45d0-9d8d-da3dbfc3930a\\all\\'  
IMAGES_FORMAT = ['.jpg', '.JPG']  
IMAGE_SIZE = 256  
IMAGE_ROW = 14  #生成图片的行
IMAGE_COLUMN =6 #生成图片的列
IMAGE_SAVE_PATH = 'D:\\Desktop\\1\\0c0b0a79-1c40-45d0-9d8d-da3dbfc3930a\\1.jpg'  #结果保存地址

#按修改时间排序
def sort_file_by_time(file_path):
    files = os.listdir(file_path)
    if not files:
        return
    else:
        files = sorted(files, key=lambda x: os.path.getmtime(os.path.join(file_path, x)))
        return files
image_names = sort_file_by_time(IMAGES_PATH)
print(image_names)

# 简单的对于参数的设定和实际图片集的大小进行数量判断
if len(image_names) > IMAGE_ROW * IMAGE_COLUMN:
    raise ValueError("不能合成图片！")
def image_compose():
    to_image = Image.new('RGB', (IMAGE_COLUMN * IMAGE_SIZE, IMAGE_ROW * IMAGE_SIZE)) 
    for y in range(1, IMAGE_ROW + 1):
        for x in range(1, IMAGE_COLUMN + 1):
            from_image = Image.open(IMAGES_PATH + image_names[IMAGE_COLUMN * (y - 1) + x - 1]).resize(
                (IMAGE_SIZE, IMAGE_SIZE),Image.ANTIALIAS)
            to_image.paste(from_image, ((x - 1) * IMAGE_SIZE, (y - 1) * IMAGE_SIZE))
    return to_image.save(IMAGE_SAVE_PATH)
image_compose() 
```

