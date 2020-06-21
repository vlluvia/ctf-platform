
# SimpleRAR


* 修改rar文件中png的文件头
> 文件块的HEAD_TYPE应该是0×74而不是0x7A。

![..](img/simplerar/simplerar1.png)

* 解压出security.png文件

![..](img/simplerar/simplerar2.png)


* Stegsolve.jar 打开图片文件，找到二维码

![..](img/simplerar/simplerar3.png)

* winhexe 查看security.png文件， 发现是gif图片

![..](img/simplerar/simplerar5.png)

* 修改图片后缀名，用ps打开，并将另一图层图片复制出

![..](img/simplerar/simplerar6.png)

* Stegsolve.jar 查看复制出的文件

![..](img/simplerar/simplerar7.png)

* ps合并两张二维码

![..](img/simplerar/simplerar8.png)

* CQR.exe 扫描二维码

![..](img/simplerar/simplerar9.png)
