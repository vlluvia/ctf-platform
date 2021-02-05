
# getit


* ida打开文件，按F5查看
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char v3; // al
  int i; // [rsp+0h] [rbp-40h]
  int j; // [rsp+4h] [rbp-3Ch]
  FILE *stream; // [rsp+8h] [rbp-38h]
  char filename[24]; // [rsp+10h] [rbp-30h] BYREF
  unsigned __int64 v9; // [rsp+28h] [rbp-18h]

  v9 = __readfsqword(0x28u);
  for ( i = 0; i < strlen(s); ++i )
  {
    if ( (i & 1) != 0 )
      v3 = 1;
    else
      v3 = -1;
    *(&t + i + 10) = s[i] + v3;
  }
  strcpy(filename, "/tmp/flag.txt");
  stream = fopen(filename, "w");
  fprintf(stream, "%s\n", u);
  for ( j = 0; j < strlen(&t); ++j )
  {
    fseek(stream, p[j], 0);
    fputc(*(&t + p[j]), stream);
    fseek(stream, 0LL, 0);
    fprintf(stream, "%s\n", u);
  }
  fclose(stream);
  remove(filename);
  return 0;
}
```


* 发现有未知的s和t，双击查看
``` 
.data:000000000060109D                 db    0
.data:000000000060109E                 db    0
.data:000000000060109F                 db    0
.data:00000000006010A0                 public s
.data:00000000006010A0 ; char s[]
.data:00000000006010A0 s               db 'c61b68366edeb7bdce3c6820314b7498',0
.data:00000000006010A0                                         ; DATA XREF: main+25↑o
.data:00000000006010A0                                         ; main+3F↑r
.data:00000000006010C1                 align 20h
.data:00000000006010E0                 public t
.data:00000000006010E0 ; char t
.data:00000000006010E0 t               db 53h                  ; DATA XREF: main+65↑w
.data:00000000006010E0                                         ; main+C9↑o ...
.data:00000000006010E1 aHarifctf       db 'harifCTF{????????????????????????????????}',0
.data:000000000060110C                 align 20h
.data:0000000000601120                 public u
.data:0000000000601120 u               db '*******************************************',0
.data:0000000000601120                                         ; DATA XREF: main+A5↑o
.data:0000000000601120                                         ; main+13F↑o
.data:000000000060114C                 align 20h
.data:0000000000601160                 public p
.data:0000000000601160 ; int p[43]
```

* 分析得到 重点的函数
``` 
  for ( i = 0; i < strlen(s); ++i )
  {
    if ( (i & 1) != 0 )
      v3 = 1;
    else
      v3 = -1;
    *(&t + i + 10) = s[i] + v3;
  }
```

* 写代码
``` 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main () {
	int i;
	char v3;
	char s[] = "c61b68366edeb7bdce3c6820314b7498";
    char t[] = "SharifCTF{????????????????????????????????}";
	for (i = 0; i < strlen(s); ++i )
  {
    if ( (i & 1) != 0 )
      v3 = 1;
    else
      v3 = -1;
	t[i+10] = s[i] + v3;
  }
	printf("%s", t);
	return 0;
}

```

* 得到flag
> SharifCTF{b70c59275fcfa8aebf2d5911223c6589}
