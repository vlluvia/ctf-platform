


# no-strings-attached


* ida查看文件，按F5
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  setlocale(6, &locale);
  banner();
  prompt_authentication();
  authenticate();
  return 0;
}
```

* authenticate()函数似乎有什么问题
``` 
void authenticate()
{
  wchar_t ws[8192]; // [esp+1Ch] [ebp-800Ch] BYREF
  wchar_t *s2; // [esp+801Ch] [ebp-Ch]

  s2 = decrypt((wchar_t *)&s, (wchar_t *)&dword_8048A90);
  if ( fgetws(ws, 0x2000, stdin) )
  {
    ws[wcslen(ws) - 1] = 0;
    if ( !wcscmp(ws, s2) )
      wprintf((int)&unk_8048B44);
    else
      wprintf((int)&unk_8048BA4);
  }
  free(s2);
}
```


* 关键点就在decrypt函数， 根据题目提示使用gdb进行调试
``` 
(No debugging symbols found in 554e0986d6db4c19b56cfdb22f13c834.exe)
(gdb) b decrypt
Breakpoint 1 at 0x804865c
(gdb) r
Starting program: /home/kali/554e0986d6db4c19b56cfdb22f13c834.exe 
Welcome to cyber malware control software.
Currently tracking 1097312000 bots worldwide

Breakpoint 1, 0x0804865c in decrypt ()
(gdb) n
Single stepping until exit from function decrypt,
which has no line number information.
0x08048725 in authenticate ()
(gdb) x/sw $eax
0x804d010:      U"9447{you_are_an_international_mystery}"

```
> b decrypt // 打断点  
> r         // 运行  
> n         // 运行到下一步  
> x/sw $eax // 查看eax寄存器

* flag
> 9447{you_are_an_international_mystery}