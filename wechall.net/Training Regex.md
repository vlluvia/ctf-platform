

# 题目1
* 题目
> 匹配空格
* 答案
> /^$/
>

# 题目2
* 题目
> 只匹配wechall

* 答案
> /^wechall$/

# 题目三
* 题目
``` 
Ok, matching static strings is not the main goal of regular expressions.
Your next task is to submit an expression that matches valid filenames for certain images.
Your pattern shall match all images with the name wechall.ext or wechall4.ext and a valid image extension.
Valid image extensions are .jpg, .gif, .tiff, .bmp and .png.
Here are some examples for valid filenames: wechall4.tiff, wechall.png, wechall4.jpg, wechall.bmp
```
* 答案
> /^wechall4?\.(?:jpg|gif|tiff|bmp|png)$/
>


# 题目四
* 题目
``` 
It is nice that we have valid images now, but could you please capture the filename, without extension, too?
As an example: wechall4.jpg should capture/return wechall4 in your pattern now.
```
* 答案
> /^(wechall4?)\.(?:jpg|gif|tiff|bmp|png)$/