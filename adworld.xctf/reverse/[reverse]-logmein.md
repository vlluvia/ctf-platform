

# logmein


* ida打开文件，找到main函数
``` 
void __fastcall __noreturn main(int a1, char **a2, char **a3)
{
  size_t v3; // rsi
  int i; // [rsp+3Ch] [rbp-54h]
  char s[36]; // [rsp+40h] [rbp-50h] BYREF
  int v6; // [rsp+64h] [rbp-2Ch]
  __int64 v7; // [rsp+68h] [rbp-28h]
  char v8[28]; // [rsp+70h] [rbp-20h] BYREF
  int v9; // [rsp+8Ch] [rbp-4h]

  v9 = 0;
  strcpy(v8, ":\"AL_RT^L*.?+6/46");
  v7 = 'ebmarah';
  v6 = 7;
  printf("Welcome to the RC3 secure password guesser.\n");
  printf("To continue, you must enter the correct password.\n");
  printf("Enter your guess: ");
  __isoc99_scanf("%32s", s);
  v3 = strlen(s);
  if ( v3 < strlen(v8) )
    sub_4007C0();
  for ( i = 0; i < strlen(s); ++i )
  {
    if ( i >= strlen(v8) )
      sub_4007C0();
    if ( s[i] != (char)(*((_BYTE *)&v7 + i % v6) ^ v8[i]) )
      sub_4007C0();
  }
  sub_4007F0();
}
```

* 代码逻辑很简单，输入一个v8长度一样的字符串，判断输入的字符串和运算后的字符串是否相等
> 注意：v7 是地址，有wp可知是字符串（按r键）

* d代码
``` 
v7 = "harambe"
v6 = 7
v8= ":\"AL_RT^L*.?+6/46"
str =''
for i  in range(len(v8)):
	str +=(chr( ord( v7 [i % v6] ) ^ ord(v8[i]) ) )
print(str)
```

* flag
> RC3-2016-XORISGUD
