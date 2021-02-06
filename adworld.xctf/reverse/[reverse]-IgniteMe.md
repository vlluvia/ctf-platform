
# IgniteMe


* ida打开文件，按F5
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  int result; // eax
  size_t i; // [esp+4Ch] [ebp-8Ch]
  char v5[8]; // [esp+50h] [ebp-88h] BYREF
  char Str[128]; // [esp+58h] [ebp-80h] BYREF

  sub_402B30(&unk_446360, "Give me your flag:");
  sub_4013F0(sub_403670);
  sub_401440(Str, 127);
  if ( strlen(Str) < 0x1E && strlen(Str) > 4 )
  {
    strcpy(v5, "EIS{");
    for ( i = 0; i < strlen(v5); ++i )
    {
      if ( Str[i] != v5[i] )
        goto LABEL_7;
    }
    if ( Str[28] != 125 )
    {
LABEL_7:
      sub_402B30(&unk_446360, "Sorry, keep trying! ");
      sub_4013F0(sub_403670);
      return 0;
    }
    if ( sub_4011C0(Str) )
      sub_402B30(&unk_446360, "Congratulations! ");
    else
      sub_402B30(&unk_446360, "Sorry, keep trying! ");
    sub_4013F0(sub_403670);
    result = 0;
  }
  else
  {
    sub_402B30(&unk_446360, "Sorry, keep trying!");
    sub_4013F0(sub_403670);
    result = 0;
  }
  return result;
}
```


* sub_4011C0函数是关键
``` 
bool __cdecl sub_4011C0(char *Str)
{
  size_t v2; // eax
  int v3; // [esp+50h] [ebp-B0h]
  char Str2[32]; // [esp+54h] [ebp-ACh] BYREF
  int v5; // [esp+74h] [ebp-8Ch]
  int v6; // [esp+78h] [ebp-88h]
  size_t i; // [esp+7Ch] [ebp-84h]
  char v8[128]; // [esp+80h] [ebp-80h] BYREF

  if ( strlen(Str) <= 4 )
    return 0;
  i = 4;
  v6 = 0;
  while ( i < strlen(Str) - 1 )
    v8[v6++] = Str[i++];
  v8[v6] = 0;
  v5 = 0;
  v3 = 0;
  memset(Str2, 0, sizeof(Str2));
  for ( i = 0; ; ++i )
  {
    v2 = strlen(v8);
    if ( i >= v2 )
      break;
    if ( v8[i] >= 97 && v8[i] <= 122 )
    {
      v8[i] -= 32;
      v3 = 1;
    }
    if ( !v3 && v8[i] >= 65 && v8[i] <= 90 )
      v8[i] += 32;
    Str2[i] = byte_4420B0[i] ^ sub_4013C0(v8[i]);
    v3 = 0;
  }
  return strcmp("GONDPHyGjPEKruv{{pj]X@rF", Str2) == 0;
}
```


* 根据函数重新写破解函数
``` 
#include<stdio.h>
#include<string.h>
#include<algorithm>
#include<vector>
#include<iostream>
#include<map>
#include<time.h>
#include<math.h>
using namespace std;
char ss[35];
//0D 13 17 11 02 01 20 1D  0C 02 19 2F 17 2B 24 1F 1E 16 09 0F 15 27 13 26  0A 2F 1E 1A 2D 0C 22 04
char s[]="GONDPHyGjPEKruv{{pj]X@rF";
int main()
{
   //bool flag=0;
    for(int i=0;i<32;i++)
        scanf("%p",&ss[i]);
        printf("EIS{");
    for(int i=0;i<strlen(s);i++)
    {
          s[i]^=ss[i];
          s[i]=(s[i]-72)^0x55;
          if(s[i]>='a'&&s[i]<='z')
              {
                  s[i]-=32;
                  continue;
              }
         if(s[i]>='A'&&s[i]<='Z')
              s[i]+=32;
    }
    printf("%s",s);
    printf("}\n");
    getchar();
    return 0;
}
```


* 得到flag
> EIS{wadx_tdgk_aihc_ihkn_pjlm}
