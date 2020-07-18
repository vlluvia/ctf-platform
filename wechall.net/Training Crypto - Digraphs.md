
* 题目
``` 
This time I am using a digraph crypto scheme to encrypt one letter into two characters.
With only 26 different letters I am able to encrypt up to 26*26 different characters.
The big problem again is sharing the key, but the cipher is easily broken anyway.
The message is in the current language, is written with correct case and punctuation. There are no line breaks.

Good luck!
```
``` 
aazsmnwcxwfqrrutarfqrrzxzsmnatwq vazsut hubnhjxwmpqurrbnhu rrpezxat yzbnatatfqwcbn atuthjhjbnatatthutararmpwq rwfqat mnzsrr rrzszs huzxththzxhjutarrr bnzxrrpebnxwoc jofqat zxrrij rwbnararoc wczszshu tszsduwq bcmnrrbnxw rrpezxat uabnmpjozsxwhu fqat atzsarutrrzxzsmnme arbnwcqupehjarzxzxwcwchjwq

```

* 代码
``` 
# 字符串每两个进行分隔，建立字典
miwen = "wglkedjkehndywqofgndywpblkedsswt nplkqo etycibehvgxyywycet ywuppbss ocycssssndjkyc ssqoibibycsssshsqofgfgvgwt qindss edlkyw ywlklk etpbhshspbibqofgyw ycpbywupycehez vbndss pbywvh qiycfgfgez jklklket oplktmwt quedywyceh ywuppbss stycvgvblkehet ndss sslkfgqoywpblkedxg fgycjkxyupibfgpbpbjkjkibwt"
miwen1 = miwen.split(" ")

dic = {'wg':'C','lk':'o','ed':'n','jk':'g','eh':'r','nd':'a','yw':'t','qo':'u','fg':'l','pb':'i','ss':'s','np':'y', 'ib':'c' ,'yc':'e', 'hs':'f','up':'h','oc':'m','et':'d'}
for i in miwen1:
    a = []
    for j in range(0, len(i), 2):
        a.append(i[j:j + 2])  # 密文字符串每两个分开
    print(a)
    b = []
    for k in a:
        if k in dic:
            b.append(dic[k])  # 解密
        else:
            b.append(' ')  # 解不出来的用空格填充
    txt = ''.join(b)
    print(txt)
```

