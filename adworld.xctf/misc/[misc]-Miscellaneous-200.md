
# Miscellaneous-200

* python 根据RGB画图
``` 

from PIL import Image

def Crack(n):#因数分解
    flag = []
    for each in range(2,int(n **0.5)+1):
        if(n % each == 0):
            print(each,int(n/each))
            flag += [(each,int(n/each))]
    if len(flag) == 1:return flag[0]
    else:
        choice = input("选择第几组(0-%s):"%(len(flag)-1))
        return flag[int(choice)]
def Paint(X,Y,listrgb):#根据字符串列表画图
    pic = Image.new("RGB",(X, Y))
    i=0
    for x in range (0,X):
        for y in range (0,Y):
            temp = listrgb[i].split(',')
            pic.putpixel([x,y],(int(temp[0]),int(temp[1]),int(temp[2])))
            i = i+1
    pic.show()
    #pic.save(r"C:\Users\ben\Desktop\flag%s.png"%(X))
listrgb = open(r"flag.txt").readlines()
X,Y = Crack(len(listrgb))
Paint(X,Y,listrgb)
Paint(Y,X,listrgb)
```

* flag
> flag{ youc@n'tseeme }