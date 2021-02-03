

# re1

* 用ida打开文件，f5查看文件,得
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  int v3; // eax
  __m128i v5; // [esp+0h] [ebp-44h] BYREF
  __int64 v6; // [esp+10h] [ebp-34h]
  int v7; // [esp+18h] [ebp-2Ch]
  __int16 v8; // [esp+1Ch] [ebp-28h]
  char v9[32]; // [esp+20h] [ebp-24h] BYREF

  v5 = _mm_loadu_si128((const __m128i *)&xmmword_413E34);
  v7 = 0;
  v6 = 0x7D465443545544i64;
  v8 = 0;
  printf("欢迎来到DUTCTF呦\n");
  printf("这是一道很可爱很简单的逆向题呦\n");
  printf("输入flag吧:");
  scanf("%s", v9);
  v3 = strcmp(v5.m128i_i8, v9);
  if ( v3 )
    v3 = v3 < 0 ? -1 : 1;
  if ( v3 )
    printf(aFlag_0);
  else
    printf((const char *const)&dword_413E90);
  system("pause");
  return 0;
}
```

* 可知输入的v9与v5.m128i_i8比较， 而v5 来自_mm_loadu_si128((const __m128i *)&xmmword_413E34);， 由此可知xmmword_413E34是字符串的地址
``` 
rdata:00413E34 xmmword_413E34  xmmword '0tem0c1eW{FTCTUD'
.rdata:00413E34                                         ; DATA XREF: _main+10↑r
.rdata:00413E44 qword_413E44    dq '}FTCTUD'            ; DATA XREF: _main+27↑r
.rdata:00413E4C ; const char aDutctf[]
.rdata:00413E4C aDutctf         db '欢迎来到DUTCTF呦',0Ah,0  ; DATA XREF: _main+1A↑o
.rdata:00413E5E                 align 10h
.rdata:00413E60 ; const char asc_413E60[]
.rdata:00413E60 asc_413E60      db '这是一道很可爱很简单的逆向题呦',0Ah,0
```
* 在xmmword_413E34行按r键可自动转成字符串（就是倒着的）
> DUTCTF{We1c0met0DUTCTF}
