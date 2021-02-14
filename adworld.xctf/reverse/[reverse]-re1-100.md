

# re1-100


* ida打开文件
``` 
int __cdecl __noreturn main(int argc, const char **argv, const char **envp)
{
  __pid_t v3; // eax
  size_t v4; // rax
  ssize_t v5; // rbx
  bool v6; // al
  bool bCheckPtrace; // [rsp+13h] [rbp-1BDh]
  ssize_t numRead; // [rsp+18h] [rbp-1B8h]
  ssize_t numReada; // [rsp+18h] [rbp-1B8h]
  char bufWrite[200]; // [rsp+20h] [rbp-1B0h] BYREF
  char bufParentRead[200]; // [rsp+F0h] [rbp-E0h] BYREF
  unsigned __int64 v12; // [rsp+1B8h] [rbp-18h]

  v12 = __readfsqword(0x28u);
  bCheckPtrace = detectDebugging();
  if ( pipe(pParentWrite) == -1 )
    exit(1);
  if ( pipe(pParentRead) == -1 )
    exit(1);
  v3 = fork();
  if ( v3 != -1 )
  {
    if ( v3 )
    {
      close(pParentWrite[0]);
      close(pParentRead[1]);
      while ( 1 )
      {
        printf("Input key : ");
        memset(bufWrite, 0, sizeof(bufWrite));
        gets(bufWrite);
        v4 = strlen(bufWrite);
        v5 = write(pParentWrite[1], bufWrite, v4);
        if ( v5 != strlen(bufWrite) )
          printf("parent - partial/failed write");
        do
        {
          memset(bufParentRead, 0, sizeof(bufParentRead));
          numReada = read(pParentRead[0], bufParentRead, 0xC8uLL);
          v6 = bCheckPtrace || checkDebuggerProcessRunning();
          if ( !v6 && checkStringIsNumber(bufParentRead) && atoi(bufParentRead) )
          {
            puts("True");
            if ( close(pParentWrite[1]) == -1 )
              exit(1);
            exit(0);
          }
          puts("Wrong !!!\n");
        }
        while ( numReada == -1 );
      }
    }
    close(pParentWrite[1]);
    close(pParentRead[0]);
    while ( 1 )
    {
      memset(bufParentRead, 0, sizeof(bufParentRead));
      numRead = read(pParentWrite[0], bufParentRead, 0xC8uLL);
      if ( numRead == -1 )
        break;
      if ( numRead )
      {
        if ( !childCheckDebugResult()
          && bufParentRead[0] == '{'
          && strlen(bufParentRead) == 42
          && !strncmp(&bufParentRead[1], "53fc275d81", '\n')
          && bufParentRead[strlen(bufParentRead) - 1] == 125
          && !strncmp(&bufParentRead[31], "4938ae4efd", '\n')
          && confuseKey(bufParentRead, 42)
          && !strncmp(bufParentRead, "{daf29f59034938ae4efd53fc275d81053ed5be8c}", 0x2AuLL) )
        {
          responseTrue();
        }
        else
        {
          responseFalse();
        }
      }
    }
    exit(1);
  }
  exit(1);
}
```


* 关键confuseKey函数
``` 
bool __cdecl confuseKey(char *szKey, int iKeyLength)
{
  char szPart1[15]; // [rsp+10h] [rbp-50h] BYREF
  char szPart2[15]; // [rsp+20h] [rbp-40h] BYREF
  char szPart3[15]; // [rsp+30h] [rbp-30h] BYREF
  char szPart4[15]; // [rsp+40h] [rbp-20h] BYREF
  unsigned __int64 v7; // [rsp+58h] [rbp-8h]

  v7 = __readfsqword(0x28u);
  *(_QWORD *)szPart1 = 0LL;
  *(_DWORD *)&szPart1[8] = 0;
  *(_WORD *)&szPart1[12] = 0;
  szPart1[14] = 0;
  *(_QWORD *)szPart2 = 0LL;
  *(_DWORD *)&szPart2[8] = 0;
  *(_WORD *)&szPart2[12] = 0;
  szPart2[14] = 0;
  *(_QWORD *)szPart3 = 0LL;
  *(_DWORD *)&szPart3[8] = 0;
  *(_WORD *)&szPart3[12] = 0;
  szPart3[14] = 0;
  *(_QWORD *)szPart4 = 0LL;
  *(_DWORD *)&szPart4[8] = 0;
  *(_WORD *)&szPart4[12] = 0;
  szPart4[14] = 0;
  if ( iKeyLength != 42 )
    return 0;
  if ( !szKey )
    return 0;
  if ( strlen(szKey) != 42 )
    return 0;
  if ( *szKey != 123 )
    return 0;
  strncpy(szPart1, szKey + 1, 0xAuLL);
  strncpy(szPart2, szKey + 11, 0xAuLL);
  strncpy(szPart3, szKey + 21, 0xAuLL);
  strncpy(szPart4, szKey + 31, 0xAuLL);
  memset(szKey, 0, 0x2AuLL);
  *szKey = 123;
  strcat(szKey, szPart3);
  strcat(szKey, szPart4);
  strcat(szKey, szPart1);
  strcat(szKey, szPart2);
  szKey[41] = 125;
  return 1;
}
```



* strcat将szPart重新重组, 得到flag
> 53fc275d81053ed5be8cdaf29f59034938ae4efd
