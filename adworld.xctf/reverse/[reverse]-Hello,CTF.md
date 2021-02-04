
# Hello, CTF


* ida打开文件，找到main函数，按F5键
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  int i; // ebx
  char v4; // al
  int result; // eax
  int v6; // [esp+0h] [ebp-70h]
  int v7; // [esp+0h] [ebp-70h]
  char Buffer[2]; // [esp+12h] [ebp-5Eh] BYREF
  char v9[20]; // [esp+14h] [ebp-5Ch] BYREF
  char v10[32]; // [esp+28h] [ebp-48h] BYREF
  __int16 v11; // [esp+48h] [ebp-28h]
  char v12; // [esp+4Ah] [ebp-26h]
  char v13[36]; // [esp+4Ch] [ebp-24h] BYREF

  strcpy(v13, "437261636b4d654a757374466f7246756e");
  while ( 1 )
  {
    memset(v10, 0, sizeof(v10));
    v11 = 0;
    v12 = 0;
    sub_40134B((int)aPleaseInputYou, v6);
    scanf("%s", v9);
    if ( strlen(v9) > 0x11 )
      break;
    for ( i = 0; i < 17; ++i )
    {
      v4 = v9[i];
      if ( !v4 )
        break;
      sprintf(Buffer, "%x", v4);
      strcat(v10, Buffer);
    }
    if ( !strcmp(v10, v13) )
      sub_40134B((int)aSuccess, v7);
    else
      sub_40134B((int)aWrong, v7);
  }
  sub_40134B((int)aWrong, v7);
  result = --Stream._cnt;
  if ( Stream._cnt < 0 )
    return _filbuf(&Stream);
  ++Stream._ptr;
  return result;
}
```

* 分析1
> if ( !strcmp(v10, v13) ) 将v10和v13是否相等

* 分析2
``` 
for ( i = 0; i < 17; ++i )
    {
      v4 = v9[i];
      if ( !v4 )
        break;
      sprintf(Buffer, "%x", v4);
      strcat(v10, Buffer);
    }
```
> %x将输入的数据转十六进制

* 在线网站解码，得到字符串就是flag
> http://ctf.ssleye.com/hex.html


* flag
> CrackMeJustForFun