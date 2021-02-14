

# Newbie_calculations

* ida打开文件
``` 
int __cdecl main(int argc, const char **argv, const char **envp)
{
  int v3; // eax
  int v4; // eax
  int v5; // eax
  int v6; // eax
  int v7; // eax
  int v8; // eax
  int v9; // eax
  int v10; // eax
  int v11; // eax
  int v12; // eax
  int v13; // eax
  int v14; // eax
  int v15; // eax
  int v16; // eax
  int v17; // eax
  int v18; // eax
  int v19; // eax
  int v20; // eax
  int v21; // eax
  int v22; // eax
  int v23; // eax
  int v24; // eax
  int v25; // eax
  int v26; // eax
  int v27; // eax
  int v28; // eax
  int v29; // eax
  int v30; // eax
  int v31; // eax
  int v32; // eax
  int v33; // eax
  int v34; // eax
  int v35; // eax
  int v36; // eax
  int v37; // eax
  int v38; // eax
  int v39; // eax
  int v40; // eax
  int v41; // eax
  int v42; // eax
  int v43; // eax
  int v44; // eax
  int v45; // eax
  int v46; // eax
  int v47; // eax
  int v48; // eax
  int v49; // eax
  int v50; // eax
  int v51; // eax
  int v52; // eax
  int v53; // eax
  int v54; // eax
  int v55; // eax
  int v56; // eax
  int v57; // eax
  int v58; // eax
  int v59; // eax
  int v60; // eax
  int v61; // eax
  int v62; // eax
  int v63; // eax
  int v64; // eax
  int v65; // eax
  int v66; // eax
  int v67; // eax
  int v68; // eax
  int v69; // eax
  int v70; // eax
  int v71; // eax
  int v72; // eax
  int v73; // eax
  int v74; // eax
  int v75; // eax
  int v76; // eax
  int v77; // eax
  int v78; // eax
  int v79; // eax
  int v80; // eax
  int v81; // eax
  int v82; // eax
  int v83; // eax
  int v84; // eax
  int v85; // eax
  int v86; // eax
  int v87; // eax
  int v88; // eax
  int v89; // eax
  int v90; // eax
  int v91; // eax
  int v92; // eax
  int v93; // eax
  int v94; // eax
  int v95; // eax
  int v96; // eax
  int v97; // eax
  int v98; // eax
  int v99; // eax
  int v100; // eax
  int v101; // eax
  int v102; // eax
  int v103; // eax
  int v104; // eax
  int v105; // eax
  int v106; // eax
  int v107; // eax
  int v108; // eax
  int v109; // eax
  int v110; // eax
  int v111; // eax
  int v112; // eax
  int v113; // eax
  int v115; // [esp-8h] [ebp-9Ch]
  int v116; // [esp-4h] [ebp-98h]
  int v117; // [esp-4h] [ebp-98h]
  int i; // [esp+4h] [ebp-90h]
  int j; // [esp+8h] [ebp-8Ch]
  int v120[12]; // [esp+Ch] [ebp-88h] BYREF
  int v121[12]; // [esp+10h] [ebp-84h] BYREF
  int v122[12]; // [esp+14h] [ebp-80h] BYREF
  int v123[12]; // [esp+18h] [ebp-7Ch] BYREF
  int v124[12]; // [esp+1Ch] [ebp-78h] BYREF
  int v125[12]; // [esp+20h] [ebp-74h] BYREF
  int v126[12]; // [esp+24h] [ebp-70h] BYREF
  int v127[12]; // [esp+28h] [ebp-6Ch] BYREF
  int v128[12]; // [esp+2Ch] [ebp-68h] BYREF
  int v129[12]; // [esp+30h] [ebp-64h] BYREF
  int v130[12]; // [esp+34h] [ebp-60h] BYREF
  int v131[12]; // [esp+38h] [ebp-5Ch] BYREF
  int v132; // [esp+3Ch] [ebp-58h] BYREF
  int v133; // [esp+40h] [ebp-54h] BYREF
  int v134; // [esp+44h] [ebp-50h] BYREF
  int v135; // [esp+48h] [ebp-4Ch] BYREF
  int v136; // [esp+4Ch] [ebp-48h] BYREF
  int v137; // [esp+50h] [ebp-44h] BYREF
  int v138; // [esp+54h] [ebp-40h] BYREF
  int v139; // [esp+58h] [ebp-3Ch] BYREF
  int v140; // [esp+5Ch] [ebp-38h] BYREF
  int v141; // [esp+60h] [ebp-34h] BYREF
  int v142; // [esp+64h] [ebp-30h] BYREF
  int v143; // [esp+68h] [ebp-2Ch] BYREF
  int v144; // [esp+6Ch] [ebp-28h] BYREF
  int v145; // [esp+70h] [ebp-24h] BYREF
  int v146; // [esp+74h] [ebp-20h] BYREF
  int v147; // [esp+78h] [ebp-1Ch] BYREF
  int v148; // [esp+7Ch] [ebp-18h] BYREF
  int v149; // [esp+80h] [ebp-14h] BYREF
  int v150; // [esp+84h] [ebp-10h] BYREF
  _DWORD v151[2]; // [esp+88h] [ebp-Ch] BYREF

  for ( i = 0; i < 32; ++i )
    v120[i] = 1;
  v151[1] = 0;
  puts("Your flag is:");
  v3 = sub_401100(v120, 1000000000);
  v4 = sub_401220(v3, 999999950);
  sub_401100(v4, 2);
  v5 = sub_401000(v121, 5000000);
  v6 = sub_401220(v5, 6666666);
  v7 = sub_401000(v6, 1666666);
  v8 = sub_401000(v7, 45);
  v9 = sub_401100(v8, 2);
  sub_401000(v9, 5);
  v10 = sub_401100(v122, 1000000000);
  v11 = sub_401220(v10, 999999950);
  v12 = sub_401100(v11, 2);
  sub_401000(v12, 2);
  v13 = sub_401000(v123, 55);
  v14 = sub_401220(v13, 3);
  v15 = sub_401000(v14, 4);
  sub_401220(v15, 1);
  v16 = sub_401100(v124, 100000000);
  v17 = sub_401220(v16, 99999950);
  v18 = sub_401100(v17, 2);
  sub_401000(v18, 2);
  v19 = sub_401220(v125, 1);
  v20 = sub_401100(v19, 1000000000);
  v21 = sub_401000(v20, 55);
  sub_401220(v21, 3);
  v22 = sub_401100(v126, 1000000);
  v23 = sub_401220(v22, 999975);
  sub_401100(v23, 4);
  v24 = sub_401000(v127, 55);
  v25 = sub_401220(v24, 33);
  v26 = sub_401000(v25, 44);
  sub_401220(v26, 11);
  v27 = sub_401100(v128, 10);
  v28 = sub_401220(v27, 5);
  v29 = sub_401100(v28, 8);
  sub_401000(v29, 9);
  v30 = sub_401000(v129, 0);
  v31 = sub_401220(v30, 0);
  v32 = sub_401000(v31, 11);
  v33 = sub_401220(v32, 11);
  sub_401000(v33, 53);
  v34 = sub_401000(v130, 49);
  v35 = sub_401220(v34, 2);
  v36 = sub_401000(v35, 4);
  sub_401220(v36, 2);
  v37 = sub_401100(v131, 1000000);
  v38 = sub_401220(v37, 999999);
  v39 = sub_401100(v38, 4);
  sub_401000(v39, 50);
  v40 = sub_401000(&v132, 1);
  v41 = sub_401000(v40, 1);
  v42 = sub_401000(v41, 1);
  v43 = sub_401000(v42, 1);
  v44 = sub_401000(v43, 1);
  v45 = sub_401000(v44, 1);
  v46 = sub_401000(v45, 10);
  sub_401000(v46, 32);
  v47 = sub_401100(&v133, 10);
  v48 = sub_401220(v47, 5);
  v49 = sub_401100(v48, 8);
  v50 = sub_401000(v49, 9);
  sub_401000(v50, 48);
  v51 = sub_401220(&v134, 1);
  v52 = sub_401100(v51, -294967296);
  v53 = sub_401000(v52, 55);
  sub_401220(v53, 3);
  v54 = sub_401000(&v135, 1);
  v55 = sub_401000(v54, 2);
  v56 = sub_401000(v55, 3);
  v57 = sub_401000(v56, 4);
  v58 = sub_401000(v57, 5);
  v59 = sub_401000(v58, 6);
  v60 = sub_401000(v59, 7);
  sub_401000(v60, 20);
  v61 = sub_401100(&v136, 10);
  v62 = sub_401220(v61, 5);
  v63 = sub_401100(v62, 8);
  v64 = sub_401000(v63, 9);
  sub_401000(v64, 48);
  v65 = sub_401000(&v137, 7);
  v66 = sub_401000(v65, 6);
  v67 = sub_401000(v66, 5);
  v68 = sub_401000(v67, 4);
  v69 = sub_401000(v68, 3);
  v70 = sub_401000(v69, 2);
  v71 = sub_401000(v70, 1);
  sub_401000(v71, 20);
  v72 = sub_401000(&v138, 7);
  v73 = sub_401000(v72, 2);
  v74 = sub_401000(v73, 4);
  v75 = sub_401000(v74, 3);
  v76 = sub_401000(v75, 6);
  v77 = sub_401000(v76, 5);
  v78 = sub_401000(v77, 1);
  sub_401000(v78, 20);
  v79 = sub_401100(&v139, 1000000);
  v80 = sub_401220(v79, 999999);
  v81 = sub_401100(v80, 4);
  v82 = sub_401000(v81, 50);
  sub_401220(v82, 1);
  v83 = sub_401220(&v140, 1);
  v84 = sub_401100(v83, -294967296);
  v85 = sub_401000(v84, 49);
  sub_401220(v85, 1);
  v86 = sub_401220(&v141, 1);
  v87 = sub_401100(v86, 1000000000);
  v88 = sub_401000(v87, 54);
  v89 = sub_401220(v88, 1);
  v90 = sub_401000(v89, 1000000000);
  sub_401220(v90, 1000000000);
  v91 = sub_401000(&v142, 49);
  v92 = sub_401220(v91, 1);
  v93 = sub_401000(v92, 2);
  sub_401220(v93, 1);
  v94 = sub_401100(&v143, 10);
  v95 = sub_401220(v94, 5);
  v96 = sub_401100(v95, 8);
  v97 = sub_401000(v96, 9);
  sub_401000(v97, 48);
  v98 = sub_401000(&v144, 1);
  v99 = sub_401000(v98, 3);
  v100 = sub_401000(v99, 3);
  v101 = sub_401000(v100, 3);
  v102 = sub_401000(v101, 6);
  v103 = sub_401000(v102, 6);
  v104 = sub_401000(v103, 6);
  sub_401000(v104, 20);
  v105 = sub_401000(&v145, 55);
  v106 = sub_401220(v105, 33);
  v107 = sub_401000(v106, 44);
  v108 = sub_401220(v107, 11);
  sub_401000(v108, 42);
  sub_401000(&v146, v145);
  sub_401000(&v147, v132);
  v115 = v147;
  v109 = sub_401220(&v148, 1);
  v110 = sub_401000(v109, v115);
  sub_401220(v110, 1);
  v116 = v143;
  v111 = sub_401220(&v149, 1);
  v112 = sub_401100(v111, 1000000);
  sub_401000(v112, v116);
  v117 = v147;
  v113 = sub_401000(&v150, 1);
  sub_401100(v113, v117);
  sub_401000(v151, v150);
  sub_401C7F("CTF{", 1);
  for ( j = 0; j < 32; ++j )
    sub_401C7F("%c", SLOBYTE(v120[j]));
  sub_401C7F("}\n");
  return 0;
}
```

* 关键 sub_401100、sub_401000、sub_401220函数
``` 
_DWORD *__cdecl sub_401220(_DWORD *a1, int a2)
{
  int v3; // [esp+8h] [ebp-10h]
  int v4; // [esp+Ch] [ebp-Ch]
  int v5; // [esp+14h] [ebp-4h]
  int v6; // [esp+14h] [ebp-4h]

  v4 = -1;
  v3 = -1 - a2 + 1;
  v5 = -1;
  while ( v3 )
  {
    ++*a1;
    --v3;
    --v5;
  }
  v6 = v5 * v5;
  while ( v4 )
  {
    v6 *= 123;
    ++*a1;
    --v4;
  }
  ++*a1;
  return a1;
}
```
``` 
_DWORD *__cdecl sub_401000(_DWORD *a1, int a2)
{
  int v3; // [esp+Ch] [ebp-18h]
  int v4; // [esp+10h] [ebp-14h]
  int v5; // [esp+18h] [ebp-Ch]
  int v6; // [esp+1Ch] [ebp-8h]

  v4 = -1;
  v3 = -1 - a2 + 1;
  v6 = 1231;
  v5 = a2 + 1231;
  while ( v3 )
  {
    ++v6;
    --*a1;
    --v3;
    --v5;
  }
  while ( v4 )
  {
    --v5;
    ++*a1;
    --v4;
  }
  ++*a1;
  return a1;
}
```

``` 
int *__cdecl sub_401100(int *a1, int a2)
{
  int v3; // [esp+Ch] [ebp-1Ch]
  int v4; // [esp+14h] [ebp-14h]
  int v5; // [esp+18h] [ebp-10h]
  int v6; // [esp+18h] [ebp-10h]
  int v7; // [esp+1Ch] [ebp-Ch]
  int v8; // [esp+20h] [ebp-8h] BYREF

  v4 = *a1;
  v5 = a2;
  v3 = -1;
  v8 = 0;
  v7 = a2 * v4;
  while ( a2 )
  {
    v6 = v7 * v4;
    sub_401000(&v8, *a1);
    ++v7;
    --a2;
    v5 = v6 - 1;
  }
  while ( v3 )
  {
    ++v7;
    ++*a1;
    --v3;
    --v5;
  }
  ++*a1;
  *a1 = v8;
  return a1;
}  
```

* wp
``` 
def mul_401100(a,b):
    return a*b
def sub_401220(a,b):
    return a-b
def add_401000(a,b):
    return a+b
flag=[1 for i in range(32)]
v121 = 0
print("Your flag is:")
v3 = mul_401100(flag[0], 0x3B9ACA00)
v4 = sub_401220(v3, 0x3B9AC9CE)
flag[0]=mul_401100(v4, 2)
v5 = add_401000(flag[1], 0x4C4B40)
v6 = sub_401220(v5, 0x65B9AA)
v7 = add_401000(v6, 1666666)
v8 = add_401000(v7, 45)
v9 = mul_401100(v8, 2)
flag[1]=add_401000(v9, 5)
v10 = mul_401100(flag[2], 0x3B9ACA00)
v11 = sub_401220(v10, 999999950)
v12 = mul_401100(v11, 2)
flag[2]=add_401000(v12, 2)
v13 = add_401000(flag[3], 55)
v14 = sub_401220(v13, 3)
v15 = add_401000(v14, 4)
flag[3]=sub_401220(v15, 1)
v16 = mul_401100(flag[4], 100000000)
v17 = sub_401220(v16, 99999950)
v18 = mul_401100(v17, 2)
flag[4]=add_401000(v18, 2)
v19 = sub_401220(flag[5], 1)
v20 = mul_401100(v19, 1000000000)
v21 = add_401000(v20, 55)
flag[5]=sub_401220(v21, 3)
v22 = mul_401100(flag[6], 1000000)
v23 = sub_401220(v22, 999975)
flag[6]=mul_401100(v23, 4)
v24 = add_401000(flag[7], 55)
v25 = sub_401220(v24, 33)
v26 = add_401000(v25, 44)
flag[7]=sub_401220(v26, 11)
v27 = mul_401100(flag[8], 10)
v28 = sub_401220(v27, 5)
v29 = mul_401100(v28, 8)
flag[8]=add_401000(v29, 9)
v30 = add_401000(flag[9], 0)
v31 = sub_401220(v30, 0)
v32 = add_401000(v31, 11)
v33 = sub_401220(v32, 11)
flag[9]=add_401000(v33, 53)
v34 = add_401000(flag[10], 49)
v35 = sub_401220(v34, 2)
v36 = add_401000(v35, 4)
flag[10]=sub_401220(v36, 2)
v37 = mul_401100(flag[11], 1000000)
v38 = sub_401220(v37, 999999)
v39 = mul_401100(v38, 4)
flag[11]=add_401000(v39, 50)
v40 = add_401000(flag[12], 1)
v41 = add_401000(v40, 1)
v42 = add_401000(v41, 1)
v43 = add_401000(v42, 1)
v44 = add_401000(v43, 1)
v45 = add_401000(v44, 1)
v46 = add_401000(v45, 10)
flag[12]=add_401000(v46, 32)
v47 = mul_401100(flag[13], 10)
v48 = sub_401220(v47, 5)
v49 = mul_401100(v48, 8)
v50 = add_401000(v49, 9)
flag[13]=add_401000(v50, 48)
v51 = sub_401220(flag[14], 1)
v52 = mul_401100(v51, -294967296)
v53 = add_401000(v52, 55)
flag[14]=sub_401220(v53, 3)
v54 = add_401000(flag[15], 1)
v55 = add_401000(v54, 2)
v56 = add_401000(v55, 3)
v57 = add_401000(v56, 4)
v58 = add_401000(v57, 5)
v59 = add_401000(v58, 6)
v60 = add_401000(v59, 7)
flag[15]=add_401000(v60, 20)
v61 = mul_401100(flag[16], 10)
v62 = sub_401220(v61, 5)
v63 = mul_401100(v62, 8)
v64 = add_401000(v63, 9)
flag[16]=add_401000(v64, 48)
v65 = add_401000(flag[17], 7)
v66 = add_401000(v65, 6)
v67 = add_401000(v66, 5)
v68 = add_401000(v67, 4)
v69 = add_401000(v68, 3)
v70 = add_401000(v69, 2)
v71 = add_401000(v70, 1)
flag[17]=add_401000(v71, 20)
v72 = add_401000(flag[18], 7)
v73 = add_401000(v72, 2)
v74 = add_401000(v73, 4)
v75 = add_401000(v74, 3)
v76 = add_401000(v75, 6)
v77 = add_401000(v76, 5)
v78 = add_401000(v77, 1)
flag[18]=add_401000(v78, 20)
v79 = mul_401100(flag[19], 1000000)
v80 = sub_401220(v79, 999999)
v81 = mul_401100(v80, 4)
v82 = add_401000(v81, 50)
flag[19]=sub_401220(v82, 1)
v83 = sub_401220(flag[20], 1)
v84 = mul_401100(v83, -294967296)
v85 = add_401000(v84, 49)
flag[20]=sub_401220(v85, 1)
v86 = sub_401220(flag[21], 1)
v87 = mul_401100(v86, 1000000000)
v88 = add_401000(v87, 54)
v89 = sub_401220(v88, 1)
v90 = add_401000(v89, 1000000000)
flag[21]=sub_401220(v90, 1000000000)
v91 = add_401000(flag[22], 49)
v92 = sub_401220(v91, 1)
v93 = add_401000(v92, 2)
flag[22]=sub_401220(v93, 1)
v94 = mul_401100(flag[23], 10)
v95 = sub_401220(v94, 5)
v96 = mul_401100(v95, 8)
v97 = add_401000(v96, 9)
flag[23]=add_401000(v97, 48)
v98 = add_401000(flag[24], 1)
v99 = add_401000(v98, 3)
v100 = add_401000(v99, 3)
v101 = add_401000(v100, 3)
v102 = add_401000(v101, 6)
v103 = add_401000(v102, 6)
v104 = add_401000(v103, 6)
flag[24]=add_401000(v104, 20)
v105 = add_401000(flag[25], 55)
v106 = sub_401220(v105, 33)
v107 = add_401000(v106, 44)
v108 = sub_401220(v107, 11)
flag[25]=add_401000(v108, 42)
flag[26]=add_401000(flag[26], flag[25])
flag[27]=add_401000(flag[27], flag[12])
v109 = flag[27]
v110 = sub_401220(flag[28], 1)
v111 = add_401000(v110, v109)
flag[28]=sub_401220(v111, 1)
v112 = flag[23]
v113 = sub_401220(flag[29], 1)
v114 = mul_401100(v113, 1000000)
flag[29]=add_401000(v114, v112)
v115 = flag[27]
v116 = add_401000(flag[30], 1)
flag[30]=mul_401100(v116, v115)
flag[31]=add_401000(flag[31], flag[30])
print("CTF{"+''.join(map(chr,flag))+"}")
```

* flag
> CTF{daf8f4d816261a41a115052a1bc21ade}