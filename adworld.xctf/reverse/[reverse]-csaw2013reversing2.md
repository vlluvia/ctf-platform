

# csaw2013reversing2


* 直接运行程序，发现乱码。ida打开文件，按F5查看
``` 
int __cdecl __noreturn main(int argc, const char **argv, const char **envp)
{
  int v3; // ecx
  CHAR *lpMem; // [esp+8h] [ebp-Ch]
  HANDLE hHeap; // [esp+10h] [ebp-4h]

  hHeap = HeapCreate(0x40000u, 0, 0);
  lpMem = (CHAR *)HeapAlloc(hHeap, 8u, SourceSize + 1);
  memcpy_s(lpMem, SourceSize, &unk_409B10, SourceSize);
  if ( !sub_40102A() && !IsDebuggerPresent() )
  {
    MessageBoxA(0, lpMem + 1, "Flag", 2u);
    HeapFree(hHeap, 0, lpMem);
    HeapDestroy(hHeap);
    ExitProcess(0);
  }
  __debugbreak();
  sub_401000(v3 + 4, lpMem);
  ExitProcess(0xFFFFFFFF);
}
```
* 分析的根据if判断进入了字符串加密，直接上od

* 在od中，search for-> All referenced strings 查看Flag
``` 
CPU Disasm
Address   Hex dump          Command                                  Comments
01191096  |>  41            INC ECX
01191097  |.  41            INC ECX
01191098  |.  41            INC ECX
01191099  |.  41            INC ECX
0119109A  |.  CC            INT3
0119109B  |.  8B55 F4       MOV EDX,DWORD PTR SS:[EBP-0C]
0119109E  |.  E8 5DFFFFFF   CALL 01191000
011910A3      EB 4A         JMP SHORT 011910EF
011910A5  /.  6A 02         PUSH 2                                   ; Type = MB_ABORTRETRYIGNORE|MB_DEFBUTTON1|MB_APPLMODAL
011910A7  |.  68 20781901   PUSH OFFSET 01197820                     ; Caption = "Flag"
011910AC  |.  FF75 F4       PUSH DWORD PTR SS:[EBP-0C]               ; Text
011910AF  |.  6A 00         PUSH 0                                   ; hOwner = NULL
011910B1  |.  FF15 E4601901 CALL DWORD PTR DS:[<&USER32.MessageBoxA>
011910B7  \.- EB 14         JMP SHORT 011910CD
011910B9  />  6A 02         PUSH 2                                   ; /Type = MB_ABORTRETRYIGNORE|MB_DEFBUTTON1|MB_APPLMODAL
011910BB  |.  68 20781901   PUSH OFFSET 01197820                     ; |Caption = "Flag"
011910C0  |.  8B45 F4       MOV EAX,DWORD PTR SS:[EBP-0C]            ; |
011910C3  |.  40            INC EAX                                  ; |
011910C4  |.  50            PUSH EAX                                 ; |Text
011910C5  |.  6A 00         PUSH 0                                   ; |hOwner = NULL
011910C7  |.  FF15 E4601901 CALL DWORD PTR DS:[<&USER32.MessageBoxA> ; \USER32.MessageBoxA

```
* 将地址011910A3中的JMP SHORT 011910EF的跳转地址改为if之后的地址也就是011910B9

``` 
CPU Disasm
Address   Hex dump          Command                                  Comments
01191094  |.-/74 23         JZ SHORT 011910B9
01191096  |> |41            INC ECX
01191097  |. |41            INC ECX
01191098  |. |41            INC ECX
01191099  |. |41            INC ECX
0119109A  |. |CC            INT3
0119109B  |. |8B55 F4       MOV EDX,DWORD PTR SS:[EBP-0C]
0119109E  |. |E8 5DFFFFFF   CALL 01191000
011910A3     |EB 14         JMP SHORT 011910B9
011910A5  /. |6A 02         PUSH 2                                   ; Type = MB_ABORTRETRYIGNORE|MB_DEFBUTTON1|MB_APPLMODAL
011910A7  |. |68 20781901   PUSH OFFSET 01197820                     ; Caption = "Flag"
011910AC  |. |FF75 F4       PUSH DWORD PTR SS:[EBP-0C]               ; Text
011910AF  |. |6A 00         PUSH 0                                   ; hOwner = NULL
011910B1  |. |FF15 E4601901 CALL DWORD PTR DS:[<&USER32.MessageBoxA>
011910B7  \.-|EB 14         JMP SHORT 011910CD
011910B9  /> \6A 02         PUSH 2                                   ; /Type = MB_ABORTRETRYIGNORE|MB_DEFBUTTON1|MB_APPLMODAL
011910BB  |.  68 20781901   PUSH OFFSET 01197820                     ; |Caption = "Flag"
011910C0  |.  8B45 F4       MOV EAX,DWORD PTR SS:[EBP-0C]            ; |

```

* F9单步运行，得到flag
> flag{reversing_is_not_that_hard!}

