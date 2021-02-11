
# reverse-for-the-holy-grail-350


* 用ida打开文件
``` 
main
int __cdecl main(int argc, const char **argv, const char **envp)
{
  int v3; // ebx
  int v4; // ebx
  __int64 v5; // rbx
  void *v7[2]; // [rsp+0h] [rbp-70h] BYREF
  _BYTE v8[16]; // [rsp+10h] [rbp-60h] BYREF
  void *v9[2]; // [rsp+20h] [rbp-50h] BYREF
  _BYTE v10[16]; // [rsp+30h] [rbp-40h] BYREF
  void *v11[2]; // [rsp+40h] [rbp-30h] BYREF
  char v12[24]; // [rsp+50h] [rbp-20h] BYREF

  v11[0] = v12;
  v11[1] = 0LL;
  v12[0] = 0;
  std::__ostream_insert<char,std::char_traits<char>>(&std::cout, "What... is your name?", 21LL);
  std::endl<char,std::char_traits<char>>(&std::cout);
  std::operator>><char>(&std::cin, v11);
  std::__ostream_insert<char,std::char_traits<char>>(&std::cout, "What... is your quest?", 22LL);
  std::endl<char,std::char_traits<char>>(&std::cout);
  std::istream::ignore((std::istream *)&std::cin);
  std::getline<char,std::char_traits<char>,std::allocator<char>>(&std::cin, v11);
  std::__ostream_insert<char,std::char_traits<char>>(&std::cout, "What...  is the secret password?", 32LL);
  std::endl<char,std::char_traits<char>>(&std::cout);
  std::operator>><char>(&std::cin, &userIn[abi:cxx11]);
  v7[0] = v8;
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::_M_construct<char *>(
    v7,
    userIn[abi:cxx11],
    qword_601AE8 + userIn[abi:cxx11]);
  v3 = validChars((__int64 *)v7);
  if ( v7[0] != v8 )
    operator delete(v7[0]);
  if ( v3 < 0 )
    goto LABEL_8;
  v9[0] = v10;
  std::__cxx11::basic_string<char,std::char_traits<char>,std::allocator<char>>::_M_construct<char *>(
    v9,
    userIn[abi:cxx11],
    qword_601AE8 + userIn[abi:cxx11]);
  v4 = stringMod(v9);
  if ( v9[0] != v10 )
    operator delete(v9[0]);
  if ( v4 < 0 )
  {
LABEL_8:
    std::__ostream_insert<char,std::char_traits<char>>(&std::cout, "Auuuuuuuugh", 11LL);
    std::endl<char,std::char_traits<char>>(&std::cout);
  }
  else
  {
    std::__ostream_insert<char,std::char_traits<char>>(&std::cout, "Go on. Off you go. tuctf{", 25LL);
    v5 = std::__ostream_insert<char,std::char_traits<char>>(&std::cout, userIn[abi:cxx11], qword_601AE8);
    std::__ostream_insert<char,std::char_traits<char>>(v5, "}", 1LL);
    std::endl<char,std::char_traits<char>>(v5);
  }
  if ( v11[0] != v12 )
    operator delete(v11[0]);
  return 0;
}

```
> stringMod
``` 
__int64 __fastcall stringMod(__int64 *a1)
{
  __int64 v1; // r9
  __int64 v2; // r10
  __int64 v3; // rcx
  int v4; // er8
  int *v5; // rdi
  int *v6; // rsi
  int v7; // ecx
  int v8; // er9
  int v9; // er10
  unsigned int v10; // eax
  int v11; // esi
  int v12; // esi
  int v14[18]; // [rsp+0h] [rbp-60h] BYREF
  __int64 v15; // [rsp+48h] [rbp-18h] BYREF

  memset(v14, 0, sizeof(v14));
  v1 = a1[1];
  if ( v1 )
  {
    v2 = *a1;
    v3 = 0LL;
    v4 = 0;
    do
    {
      v12 = *(char *)(v2 + v3);
      v14[v3] = v12;
      if ( 3 * ((unsigned int)v3 / 3) == (_DWORD)v3 && v12 != firstchar[(unsigned int)v3 / 3] )
        v4 = -1;
      ++v3;
    }
    while ( v3 != v1 );
  }
  else
  {
    v4 = 0;
  }
  v5 = v14;
  v6 = v14;
  v7 = 666;
  do
  {
    *v6 = v7 ^ *(unsigned __int8 *)v6;
    v7 += v7 % 5;
    ++v6;
  }
  while ( &v15 != (__int64 *)v6 );
  v8 = 1;
  v9 = 0;
  v10 = 1;
  v11 = 0;
  do
  {
    if ( v11 == 2 )
    {
      if ( *v5 != thirdchar[v9] )
        v4 = -1;
      if ( v10 % *v5 != masterArray[v9] )
        v4 = -1;
      ++v9;
      v10 = 1;
      v11 = 0;
    }
    else
    {
      v10 *= *v5;
      if ( ++v11 == 3 )
        v11 = 0;
    }
    ++v8;
    ++v5;
  }
  while ( v8 != 19 );
  return (unsigned int)(v7 * v4);
}
```


* 编写代码
``` 
i = 666
num = []                                       # v7
flag = 'A**i**n**E**o**a**'           # flag第0+3*n位对应firstchar
Xorflag = []                                   # flag每位与v7异或的结果
thirdchar = [0x2ef, 0x2c4, 0x2dc, 0x2c7, 0x2de, 0x2fc]
masterarray = [0x1d7, 0xc, 0x244, 0x25e, 0x93, 0x6c]
for j in range(18):                         # 求v7
    num.append(i)
    i += (i % 5)
temp_num = 0
for i in range(2, len(flag)+1, 3):        # 求flag 第 1+3*n位
    temp = thirdchar[temp_num] ^ num[i]
    temp_num += 1
    flag = flag[:i] + chr(temp) + flag[i+1:]
temp_num = 0
for i in range(len(flag)):                 # flag每位与v7异或
    temp = ord(flag[i]) ^ num[i]
    Xorflag.append(temp)
for i in range(1, 19, 3):                    # 求flag第1+3*n位
    for j in range(32, 128):
        j ^= num[i]
        temp = j * Xorflag[i-1] % Xorflag[i+1]
        if temp == masterarray[temp_num]:
            flag = flag[:i] + chr(j ^ num[i]) + flag[i+1:]
            temp_num += 1
            break
print("tuctf{" + flag + '}')
```

* flag
> tuctf{AfricanOrEuropean?}