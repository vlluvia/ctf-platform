

# re-for-50-plz-50


* ida打开文件，找到main函数，按F5
``` 
int __cdecl __noreturn main(int argc, const char **argv, const char **envp)
{
  int i; // [sp+18h] [+18h]

  for ( i = 0; i < 31; ++i )
  {
    if ( meow[i] != (char)(argv[1][i] ^ 0x37) )
    {
      print("NOOOOOOOOOOOOOOOOOO\n");
      exit_funct();
    }
  }
  puts("C0ngr4ssulations!! U did it.", argv, envp);
  exit_funct();
}
```

* if函数是关键，其中meow数组进行更进
> if ( meow[i] != (char)(argv[1][i] ^ 0x37) )  
> .data:004A3720 meow:           .ascii "cbtcqLUBChERV[[Nh@_X^D]X_YPV[CJ"<0>


* 编写破解代码
``` 
# _*_ coding: utf-8 _*
str = "cbtcqLUBChERV[[Nh@_X^D]X_YPV[CJ"

res = ""
for i in range(31):
    res += chr(ord(str[i]) ^ 0x37)

print(res)
```
