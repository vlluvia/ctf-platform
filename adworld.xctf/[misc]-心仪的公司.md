
# 心仪的公司

* wireshark 分析数据包， 发现conf1g.php 是webshell
> tcp.stream eq 473


* 方法二: 
> strings webshell.pcapng | grep “^f”

