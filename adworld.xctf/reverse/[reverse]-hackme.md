

# hackme


* ida打开文件,sub_400F8E函数有代码
``` 
__int64 __fastcall sub_400F8E(__int64 a1, int a2, int a3, int a4, int a5, int a6)
{
  int v6; // edx
  int v7; // ecx
  int v8; // er8
  int v9; // er9
  int v10; // ecx
  int v11; // er8
  int v12; // er9
  char v14; // [rsp+0h] [rbp-C0h]
  char v15; // [rsp+0h] [rbp-C0h]
  char v16[136]; // [rsp+10h] [rbp-B0h] BYREF
  int v17; // [rsp+98h] [rbp-28h]
  char v18; // [rsp+9Fh] [rbp-21h]
  int v19; // [rsp+A0h] [rbp-20h]
  unsigned __int8 v20; // [rsp+A6h] [rbp-1Ah]
  char v21; // [rsp+A7h] [rbp-19h]
  int v22; // [rsp+A8h] [rbp-18h]
  int v23; // [rsp+ACh] [rbp-14h]
  int v24; // [rsp+B0h] [rbp-10h]
  int v25; // [rsp+B4h] [rbp-Ch]
  _BOOL4 v26; // [rsp+B8h] [rbp-8h]
  int i; // [rsp+BCh] [rbp-4h]

  sub_407470((unsigned int)"Give me the password: ", a2, a3, a4, a5, a6, a2);
  sub_4075A0((unsigned int)"%s", (unsigned int)v16, v6, v7, v8, v9, v14);
  for ( i = 0; v16[i]; ++i )
    ;
  v26 = i == 22;
  v25 = 10;
  do
  {
    v10 = (int)sub_406D90() % 22;
    v22 = v10;
    v24 = 0;
    v21 = byte_6B4270[v10];
    v20 = v16[v10];
    v19 = v10 + 1;
    v23 = 0;
    while ( v23 < v19 )
    {
      ++v23;
      v24 = 1828812941 * v24 + 12345;
    }
    v18 = v24 ^ v20;
    if ( v21 != ((unsigned __int8)v24 ^ v20) )
      v26 = 0;
    --v25;
  }
  while ( v25 );
  if ( v26 )
    v17 = sub_407470((unsigned int)"Congras\n", (unsigned int)v16, v24, v10, v11, v12, v15);
  else
    v17 = sub_407470((unsigned int)"Oh no!\n", (unsigned int)v16, v24, v10, v11, v12, v15);
  return 0LL;
}
```

* 查看wp，sub_406D90函数是生成随机数， 验证输入22位-->生成随机数验证10位数

``` 
bs=[0x5F, 0xF2, 0x5E, 0x8B, 0x4E, 0x0E, 0xA3, 0xAA, 0xC7, 0x93,
  0x81, 0x3D, 0x5F, 0x74, 0xA3, 0x09, 0x91, 0x2B, 0x49, 0x28,
  0x93, 0x67]
flag=[0 for i in range(22)]
for index in range(22):
    b=bs[index]
    temp=0
    for i in range(index+1):
        temp=(0x6D01788D * temp + 0x3039)
    flag[index]=(temp^b)&0xff
print(''.join(map(chr,flag)))
```


* 生成flag
> flag{d826e6926098ef46}