
# game


* ida打开文件，查找到主函数
> 方法：
> 1. 点击 Function window -> Function name  
> 2. Search-> 输入main

* 按F5
``` 
int __cdecl main_0(int argc, const char **argv, const char **envp)
{
  int i; // [esp+DCh] [ebp-20h]
  int v5; // [esp+F4h] [ebp-8h] BYREF

  sub_45A7BE(&unk_50B110);
  sub_45A7BE(&unk_50B158);
  sub_45A7BE(&unk_50B1A0);
  sub_45A7BE(&unk_50B1E8);
  sub_45A7BE(&unk_50B230);
  sub_45A7BE(&unk_50B278);
  sub_45A7BE(&unk_50B2C0);
  sub_45A7BE(&unk_50B308);
  sub_45A7BE("二                                                     |\n");
  sub_45A7BE("|              by 0x61                                 |\n");
  sub_45A7BE("|                                                      |\n");
  sub_45A7BE("|------------------------------------------------------|\n");
  sub_45A7BE(
    "Play a game\n"
    "The n is the serial number of the lamp,and m is the state of the lamp\n"
    "If m of the Nth lamp is 1,it's on ,if not it's off\n"
    "At first all the lights were closed\n");
  sub_45A7BE("Now you can input n to change its state\n");
  sub_45A7BE(
    "But you should pay attention to one thing,if you change the state of the Nth lamp,the state of (N-1)th and (N+1)th w"
    "ill be changed too\n");
  sub_45A7BE("When all lamps are on,flag will appear\n");
  sub_45A7BE("Now,input n \n");
  while ( 1 )
  {
    while ( 1 )
    {
      sub_45A7BE("input n,n(1-8)\n");
      sub_459418();
      sub_45A7BE("n=");
      sub_4596D4("%d", &v5);
      sub_45A7BE("\n");
      if ( v5 >= 0 && v5 <= 8 )
        break;
      sub_45A7BE("sorry,n error,try again\n");
    }
    if ( v5 )
    {
      sub_4576D6(v5 - 1);
    }
    else
    {
      for ( i = 0; i < 8; ++i )
      {
        if ( (unsigned int)i >= 9 )
          j____report_rangecheckfailure();
        byte_532E28[i] = 0;
      }
    }
    j__system("CLS");
    sub_458054();
    if ( byte_532E28[0] == 1
      && byte_532E28[1] == 1
      && byte_532E28[2] == 1
      && byte_532E28[3] == 1
      && byte_532E28[4] == 1
      && byte_532E28[5] == 1
      && byte_532E28[6] == 1
      && byte_532E28[7] == 1 )
    {
      sub_457AB4();
    }
  }
}
```
* 分析sub_457AB4()函数应该就是flag

* 跟进函数，得到加密函数（不知道为什么，本人的反编译代码是有问题（64位win10加ida32），网上查了wp重新获得正确的代码）
``` 
// 上面的实质数据是有问题的
 for ( i = 0; i < 56; ++i )
  {
    v2[i] ^= v5[i];
    v2[i] ^= 0x13u;
  }
```

* 重写代码
``` 
xor=[18,64,98,5,2,4,6,3,6,48,49,65,32,12,48,65,31,78,62,32,49,32,1,57,96,3,21,9,4,62,3,5,4,1,2,3,44,65,78,32,16,97,54,16,44,52,32,64,89,45,32,65,15,34,18,16,0]
key=[123, 32, 18, 98, 119, 108, 65, 41, 124, 80, 125, 38, 124, 111, 74, 49, 83, 108, 94, 108, 84, 6, 96, 83, 44, 121, 104, 110, 32, 95, 117, 101, 99, 123, 127, 119, 96, 48, 107, 71, 92, 29, 81, 107, 90, 85, 64, 12, 43, 76, 86, 13, 114, 1, 117, 126, 0]

flag=''
for i in range(56):
    a = key[i]
    a ^= 0x13
    a ^= xor[i]
    flag += chr(a)

print(flag)
```

* flag
> zsctf{T9is_tOpic_1s_v5ry_int7resting_b6t_others_are_n0t}
