

# crazy

* ida打开文件，按F5反汇编
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  __int64 v3; // rax
  __int64 v4; // rax
  __int64 v5; // rax
  __int64 v6; // rax
  __int64 v7; // rax
  __int64 v8; // rax
  __int64 v9; // rax
  __int64 v10; // rax
  __int64 v11; // rax
  __int64 v12; // rax
  __int64 v13; // rax
  __int64 v14; // rax
  __int64 v15; // rax
  __int64 v16; // rax
  char v18[32]; // [rsp+10h] [rbp-130h] BYREF
  char v19[32]; // [rsp+30h] [rbp-110h] BYREF
  char v20[32]; // [rsp+50h] [rbp-F0h] BYREF
  char v21[32]; // [rsp+70h] [rbp-D0h] BYREF
  char v22[32]; // [rsp+90h] [rbp-B0h] BYREF
  char v23[120]; // [rsp+B0h] [rbp-90h] BYREF
  unsigned __int64 v24; // [rsp+128h] [rbp-18h]

  v24 = __readfsqword(0x28u);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::basic_string(v18, argv, envp);
  std::operator>><char>(&std::cin, v18);
  v3 = std::operator<<<std::char_traits<char>>(&std::cout, "-------------------------------------------");
  std::ostream::operator<<(v3, &std::endl<char,std::char_traits<char>>);
  v4 = std::operator<<<std::char_traits<char>>(&std::cout, "Quote from people's champ");
  std::ostream::operator<<(v4, &std::endl<char,std::char_traits<char>>);
  v5 = std::operator<<<std::char_traits<char>>(&std::cout, "-------------------------------------------");
  std::ostream::operator<<(v5, &std::endl<char,std::char_traits<char>>);
  v6 = std::operator<<<std::char_traits<char>>(
         &std::cout,
         "*My goal was never to be the loudest or the craziest. It was to be the most entertaining.");
  std::ostream::operator<<(v6, &std::endl<char,std::char_traits<char>>);
  v7 = std::operator<<<std::char_traits<char>>(&std::cout, "*Wrestling was like stand-up comedy for me.");
  std::ostream::operator<<(v7, &std::endl<char,std::char_traits<char>>);
  v8 = std::operator<<<std::char_traits<char>>(
         &std::cout,
         "*I like to use the hard times in the past to motivate me today.");
  std::ostream::operator<<(v8, &std::endl<char,std::char_traits<char>>);
  v9 = std::operator<<<std::char_traits<char>>(&std::cout, "-------------------------------------------");
  std::ostream::operator<<(v9, &std::endl<char,std::char_traits<char>>);
  HighTemplar::HighTemplar(v23, v18);
  v10 = std::operator<<<std::char_traits<char>>(&std::cout, "Checking....");
  std::ostream::operator<<(v10, &std::endl<char,std::char_traits<char>>);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::basic_string((__int64)v19, (__int64)v18);
  func1(v20, v19);
  func2((__int64)v21, (__int64)v20);
  func3((__int64)v21, 0);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::~basic_string(v21);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::~basic_string(v20);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::~basic_string(v19);
  HighTemplar::calculate((HighTemplar *)v23);
  if ( !(unsigned int)HighTemplar::getSerial((HighTemplar *)v23) )
  {
    v11 = std::operator<<<std::char_traits<char>>(&std::cout, "/////////////////////////////////");
    std::ostream::operator<<(v11, &std::endl<char,std::char_traits<char>>);
    v12 = std::operator<<<std::char_traits<char>>(&std::cout, "Do not be angry. Happy Hacking :)");
    std::ostream::operator<<(v12, &std::endl<char,std::char_traits<char>>);
    v13 = std::operator<<<std::char_traits<char>>(&std::cout, "/////////////////////////////////");
    std::ostream::operator<<(v13, &std::endl<char,std::char_traits<char>>);
    HighTemplar::getFlag[abi:cxx11]((__int64)v22, (__int64)v23);
    v14 = std::operator<<<std::char_traits<char>>(&std::cout, "flag{");
    v15 = std::operator<<<char>(v14, v22);
    v16 = std::operator<<<std::char_traits<char>>(v15, "}");
    std::ostream::operator<<(v16, &std::endl<char,std::char_traits<char>>);
    std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::~basic_string(v22);
  }
  HighTemplar::~HighTemplar((HighTemplar *)v23);
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::~basic_string(v18);
  return 0;
}
```


* 关键函数calculate
``` 
bool __fastcall HighTemplar::calculate(HighTemplar *this)
{
  __int64 v1; // rax
  _BYTE *v2; // rbx
  bool result; // al
  _BYTE *v4; // rbx
  int i; // [rsp+18h] [rbp-18h]
  int j; // [rsp+1Ch] [rbp-14h]

  if ( std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::length((char *)this + 16) != 32 )
  {
    v1 = std::operator<<<std::char_traits<char>>(&std::cout, "Too short or too long");
    std::ostream::operator<<(v1, &std::endl<char,std::char_traits<char>>);
    exit(-1);
  }
  for ( i = 0;
        i <= (unsigned __int64)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::length((char *)this + 16);
        ++i )
  {
    v2 = (_BYTE *)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::operator[](
                    (char *)this + 16,
                    i);
    *v2 = (*(_BYTE *)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::operator[](
                       (char *)this + 16,
                       i) ^ 0x50)
        + 23;
  }
  for ( j = 0; ; ++j )
  {
    result = j <= (unsigned __int64)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::length((char *)this + 16);
    if ( !result )
      break;
    v4 = (_BYTE *)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::operator[](
                    (char *)this + 16,
                    j);
    *v4 = (*(_BYTE *)std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::operator[](
                       (char *)this + 16,
                       j) ^ 0x13)
        + 11;
  }
  return result;
}
```

* 分析得到先异或后加减
``` 
code = list("327a6c4304ad5938eaf0efb6cc3e53dc")
 
for i in range(32):
    code[i] = chr((ord(code[i])-11)^0x13)
 
for i in range(32):
    code[i] = chr((ord(code[i])-23)^0x50)
 
print("".join(code))
```

* 运行后
> tMx~qdstOs~crvtwb~aOba}qddtbrtcd


* 带入程序运行
>  flag{tMx~qdstOs~crvtwb~aOba}qddtbrtcd}