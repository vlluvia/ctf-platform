
# latlong

* 【原理】
> 分析波形文件
  
* 【目的】
> 利用提示中传输协议分析文件
  
* 【环境】
> windows
  
* 【工具】
> audacity,multimon-ng
  
* 【步骤】
1. 步骤1：
```
  先用file发现附件为一个WAV格式的音频文件，所以先用Audacity打开。
  
  Alt text
  
  发现在1100Hz和2200Hz出现了峰值。推测与提示中的AX.25有关。
```

* 步骤2：
> 利用multimon-ng对文件进行分析
``` 

# ./multimon-ng -t raw -a AFSK1200 transmission.raw

multimon-ng (C) 1996/1997 by Tom Sailer HB9JNX/AE4WA (C) 2012-2014 by Elias
Oenal available demodulators: POCSAG512 POCSAG1200 POCSAG2400 FLEX EAS
UFSK1200 CLIPFSK FMSFSK AFSK1200 AFSK2400 AFSK2400_2 AFSK2400_3 HAPN4800
FSK9600 DTMF ZVEI1 ZVEI2 ZVEI3 DZVEI PZVEI EEA EIA CCIR MORSE_CW DUMPCSV SCOPE
Enabled demodulators: AFSK1200 AFSK1200: fm WDPX01-0 to APRS-0 UI pid=F0
!/;E'q/Sz'O /A=000000flag{f4ils4f3c0mms} ```

得到flag

## 【总结】
```