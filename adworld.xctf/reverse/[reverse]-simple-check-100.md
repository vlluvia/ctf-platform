
# simple-check-100

* ida打开文件，按F5
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  void *v3; // esp
  void *v4; // esp
  char v6; // [esp+8h] [ebp-40h] BYREF
  char v7; // [esp+1Bh] [ebp-2Dh] BYREF
  char *v8; // [esp+1Ch] [ebp-2Ch]
  int v9; // [esp+20h] [ebp-28h]
  char v10; // [esp+25h] [ebp-23h]
  char v11; // [esp+26h] [ebp-22h]
  char v12; // [esp+27h] [ebp-21h]
  char v13; // [esp+28h] [ebp-20h]
  char v14; // [esp+29h] [ebp-1Fh]
  char v15; // [esp+2Ah] [ebp-1Eh]
  char v16; // [esp+2Bh] [ebp-1Dh]
  char v17; // [esp+2Ch] [ebp-1Ch]
  char v18; // [esp+2Dh] [ebp-1Bh]
  char v19; // [esp+2Eh] [ebp-1Ah]
  char v20; // [esp+2Fh] [ebp-19h]
  char v21; // [esp+30h] [ebp-18h]
  char v22; // [esp+31h] [ebp-17h]
  char v23; // [esp+32h] [ebp-16h]
  char v24; // [esp+33h] [ebp-15h]
  char v25; // [esp+34h] [ebp-14h]
  char v26; // [esp+35h] [ebp-13h]
  char v27; // [esp+36h] [ebp-12h]
  char v28; // [esp+37h] [ebp-11h]
  char v29; // [esp+38h] [ebp-10h]
  char v30; // [esp+39h] [ebp-Fh]
  char v31; // [esp+3Ah] [ebp-Eh]
  char v32; // [esp+3Bh] [ebp-Dh]
  char v33; // [esp+3Ch] [ebp-Ch]
  char v34; // [esp+3Dh] [ebp-Bh]
  char v35; // [esp+3Eh] [ebp-Ah]
  char v36; // [esp+3Fh] [ebp-9h]
  int *v37; // [esp+40h] [ebp-8h]

  v37 = &argc;
  __main();
  v7 = 84;
  v36 = -56;
  v35 = 126;
  v34 = -29;
  v33 = 100;
  v32 = -57;
  v31 = 22;
  v30 = -102;
  v29 = -51;
  v28 = 17;
  v27 = 101;
  v26 = 50;
  v25 = 45;
  v24 = -29;
  v23 = -45;
  v22 = 67;
  v21 = -110;
  v20 = -87;
  v19 = -99;
  v18 = -46;
  v17 = -26;
  v16 = 109;
  v15 = 44;
  v14 = -45;
  v13 = -74;
  v12 = -67;
  v11 = -2;
  v10 = 106;
  v9 = 19;
  v3 = alloca(32);
  v4 = alloca(32);
  v8 = &v6;
  printf("Key: ");
  scanf("%s", v8);
  if ( check_key(v8) )
    interesting_function((int)&v7);
  else
    puts("Wrong");
  return 0;
}
```

* check_key有异常，跟进
``` 
BOOL __cdecl check_key(int a1)
{
  int i; // [esp+8h] [ebp-8h]
  int v3; // [esp+Ch] [ebp-4h]

  v3 = 0;
  for ( i = 0; i <= 4; ++i )
    v3 += *(_DWORD *)(4 * i + a1);
  return v3 == '\xDE\xAD\xBE\xEF';
}
```

* gdb打开文件，动态调试
``` 
gdb

file task9_x86_64_46d01fe312d35ecf69c4ff8ab8ace75d080891dc

b main

r
```

* 单步到check函数，把test eax,eax改为真就行，也就是把eax改为1。
``` 
set $eax=1
```


* 运行完，得到flag
> flag_is_you_know_cracking!!!

