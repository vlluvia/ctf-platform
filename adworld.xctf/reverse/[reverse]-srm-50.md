
# srm-50

* ida打开文件，在main函数按F5
``` 
int __stdcall WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nShowCmd)
{
  return DialogBoxParamW(hInstance, (LPCWSTR)0x65, 0, DialogFunc, 0);
}
```


* 跟踪DialogFunc函数
``` 
INT_PTR __stdcall DialogFunc(HWND hDlg, UINT a2, WPARAM a3, LPARAM a4)
{
  HMODULE v5; // eax
  HICON v6; // eax
  HMODULE v7; // eax
  HWND v8; // eax
  HCURSOR v9; // [esp-4h] [ebp-34Ch]
  CHAR String[256]; // [esp+8h] [ebp-340h] BYREF
  CHAR v11[256]; // [esp+108h] [ebp-240h] BYREF
  CHAR Text[256]; // [esp+208h] [ebp-140h] BYREF
  char Source[60]; // [esp+308h] [ebp-40h] BYREF

  if ( a2 == 16 )
  {
    EndDialog(hDlg, 0);
    return 0;
  }
  if ( a2 == 272 )
  {
    v5 = GetModuleHandleW(0);
    v6 = LoadIconW(v5, (LPCWSTR)0x67);
    SetClassLongA(hDlg, -14, (LONG)v6);
    v7 = GetModuleHandleW(0);
    v9 = LoadCursorW(v7, (LPCWSTR)0x66);
    v8 = GetDlgItem(hDlg, 1);
    SetClassLongA(v8, -12, (LONG)v9);
    return 1;
  }
  if ( a2 != 273 || (unsigned __int16)a3 != 1 )
    return 0;
  memset(String, (unsigned __int16)a3 - 1, sizeof(String));
  memset(v11, 0, sizeof(v11));
  memset(Text, 0, sizeof(Text));
  GetDlgItemTextA(hDlg, 1001, String, 256);
  GetDlgItemTextA(hDlg, 1002, v11, 256);
  if ( strstr(String, "@") && strstr(String, ".") && strstr(String, ".")[1] && strstr(String, "@")[1] != 46 )
  {
    strcpy(&Source[36], "Registration failure.");
    strcpy(Source, "Registration Success!\nYour flag is:");
    if ( strlen(v11) == 16
      && v11[0] == 'C'
      && v11[15] == 'X'
      && v11[1] == 'Z'
      && v11[14] == 'A'
      && v11[2] == '9'
      && v11[13] == 'b'
      && v11[3] == 'd'
      && v11[12] == '7'
      && v11[4] == 'm'
      && v11[11] == 'G'
      && v11[5] == 'q'
      && v11[10] == '9'
      && v11[6] == '4'
      && v11[9] == 'g'
      && v11[7] == 'c'
      && v11[8] == '8' )
    {
      strcpy_s(Text, 0x100u, Source);
      strcat_s(Text, 0x100u, v11);
    }
    else
    {
      strcpy_s(Text, 0x100u, &Source[36]);
    }
  }
  else
  {
    strcpy_s(Text, 0x100u, "Your E-mail address in not valid.");
  }
  MessageBoxA(hDlg, Text, "Registeration", 0x40u);
  return 1;
}
```

* Registration Success!\nYour flag is表明接下来if函数就是flag
> CZ9dmq4c8g9G7bAX
