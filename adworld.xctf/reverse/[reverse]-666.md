
# 666


* ida打开文件，按F5
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char s[240]; // [rsp+0h] [rbp-1E0h] BYREF
  char v5[240]; // [rsp+F0h] [rbp-F0h] BYREF

  memset(s, 0, 0x1EuLL);
  printf("Please Input Key: ");
  __isoc99_scanf("%s", v5);
  encode(v5, (__int64)s);
  if ( strlen(v5) == key )
  {
    if ( !strcmp(s, enflag) )
      puts("You are Right");
    else
      puts("flag{This_1s_f4cker_flag}");
  }
  return 0;
}
```
* 分析encode函数是关键，追踪下去
``` 
int __fastcall encode(const char *a1, __int64 a2)
{
  char v3[104]; // [rsp+10h] [rbp-70h]
  int v4; // [rsp+78h] [rbp-8h]
  int i; // [rsp+7Ch] [rbp-4h]

  i = 0;
  v4 = 0;
  if ( strlen(a1) != key )
    return puts("Your Length is Wrong");
  for ( i = 0; i < key; i += 3 )
  {
    v3[i + 64] = key ^ (a1[i] + 6);
    v3[i + 33] = (a1[i + 1] - 6) ^ key;
    v3[i + 2] = a1[i + 2] ^ 6 ^ key;
    *(_BYTE *)(a2 + i) = v3[i + 64];
    *(_BYTE *)(a2 + i + 1LL) = v3[i + 33];
    *(_BYTE *)(a2 + i + 2LL) = v3[i + 2];
  }
  return a2;
}
```

* 根据代码思路，我们自己写解密的函数
``` 
enflag = 'izwhroz""w"v.K".Ni'
key = 0x12
v = []
flag = ''
for i in range(0, key, 3):
    a = (ord(enflag[i]) ^ key) - 6
    b = (ord(enflag[i+1]) ^ key) + 6
    c = ord(enflag[i+2]) ^ 6 ^ key
    v.append(a)
    v.append(b)
    v.append(c)

for i in v:
    flag += chr(i)

print(flag)
```



* 得到flag
> unctf{b66_6b6_66b}