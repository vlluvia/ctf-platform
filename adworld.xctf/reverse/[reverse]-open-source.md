
# open-source

* 查看源码
``` 
#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
    if (argc != 4) {            
    	printf("what?\n");
    	exit(1);
    }

    unsigned int first = atoi(argv[1]);
    if (first != 0xcafe) {      //要求二
    	printf("you are wrong, sorry.\n");
    	exit(2);
    }

    unsigned int second = atoi(argv[2]);
    if (second % 5 == 3 || second % 17 != 8) {
    	printf("ha, you won't get it!\n"); 
    	exit(3);
    }

    if (strcmp("h4cky0u", argv[3])) {
    	printf("so close, dude!\n");    
    	exit(4);
    }

    printf("Brr wrrr grr\n");

    unsigned int hash = first * 31337 + (second % 17) * 11 + strlen(argv[3]) - 1615810207;

    printf("Get your key: ");
    printf("%x\n", hash);
    return 0;
}

```

* 分析1
``` 
    if (argc != 4) {            
    	printf("what?\n");
    	exit(1);
    }
```
> 参数有四个，没什么用

*  分析2
``` 
    unsigned int first = atoi(argv[1]);
    if (first != 0xcafe) {      //要求二
    	printf("you are wrong, sorry.\n");
    	exit(2);
    }
```
> first = 0xcafe

*  分析3
``` 
    unsigned int second = atoi(argv[2]);
    if (second % 5 == 3 || second % 17 != 8) {
    	printf("ha, you won't get it!\n"); 
    	exit(3);
    }
```
> 被5余不能等于3，同时被17余等于8  
> second = 25

* 分析4
``` 
    if (strcmp("h4cky0u", argv[3])) {
    	printf("so close, dude!\n");    
    	exit(4);
    }
```
> argv[3] = "h4cky0u"


* 总结
``` 
first = 0xcafe;
second = 25; // 循环
three = "h4cky0u";
hash = first * 31337 + (second % 17) * 11 + strlen(three) - 1615810207;

print(hex(hash));
```

* flag
> c0ffee