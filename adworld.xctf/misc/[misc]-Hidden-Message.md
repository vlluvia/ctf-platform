
# Hidden-Message


* [原理]
> tshark
  
* [目地]
> 认识隐写术的一种方式
  
* [环境]
> Linux
  
* [工具]
> tshark
  
* [步骤]
1. 这个包里面有一个和Classical Physics Wiki page(http://en.wikipedia.org/wiki/Classical_physics#Comparison_with_modern_physics)的数据交换。
2. 我们可以用这条命令来解释payload：
> $ tshark -r hidden-message.pcap -Tfields -e data | xxd -r -p In contrast to classical physics modern physics is a slightly looser term which may refer to just quantum physics or to 20th and 21st century physics in general and so always includes quantum theory and may include relativity A physical system on the classical level is a physical system in which the laws of classical physics are valid There are no restrictions on the application of classical principles but practically the scale of classical physics is the level of isolated atoms and molecules on upwards including the macroscopic and astronomical realm Inside the atom and among atoms in a molecule the laws of classical physics break down and generally do not provide a correct description Moreover the classical theory of electromagnetic radiation is somewhat limited in its ability to provide correct descriptions since quantum effects are observable in more everyday circumstances than quantum effects of matter Unlike quantum physics classical physics is generally characterized by the principle of complete determinism although the Manyworlds interpretation of quantum mechanics is in a sense deterministic Mathematically classical physics equations are ones in which Plancks constant does not appear According to the correspondence principle and Ehrenfests theorem as a system becomes larger or more massive action Plancks constant the classical dynamics tends to emerge with some exceptions such as superfluidity This is why we can usually ignore quantum mechanics when dealing with everyday objects instead the classical description will suffice However one of the most vigorous ongoing fields of research in physics is classicalquantum correspondence This field of research is concerned with the discovery of how the laws of quantum physics give rise to classical physics in the limit of the large scales of the classical le
3. 我们可以看到源端口的末尾数字在0和1之间变换，所以我们可以用tshark和perl来解析这段数据。
> bash $ tshark -r hidden-message.pcap -Tfields -e udp.srcport | while read port; do echo -n ${port: -1}; done | perl -lpe '$_=pack"B*",$_' ??????????
4. 不是很完整。所以我们用tr来转化为二进制输出在评估二进制输出之前。
> bash $ tshark -r hidden-message.pcap -Tfields -e udp.srcport | while read port; do echo -n ${port: -1}; done | tr 01 10 | perl -lpe '$_=pack"B*",$_' Heisenberg

* [结果]
> FLAGHeisenberg

