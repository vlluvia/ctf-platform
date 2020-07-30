

# NaNNaNNaNNaN-Batman


* 解压有的文件里有乱码，改成后缀为.html文件，

* 修改脚本中最后的EVAL改成alert，浏览器打开脚本
``` 
function $(){
var e=document.getElementById("c").value;
if(e.length==16)
	if(e.match(/^be0f23/)!=null)
		if(e.match(/233ac/)!=null)
			if(e.match(/e98aa$/)!=null)
				if(e.match(/c7be9/)!=null){
					var t=["fl","s_a","i","e}"];
					var n=["a","_h0l","n"];
					var r=["g{","e","_0"];
					var i=["it'","_","n"];
					var s=[t,n,r,i];
					for(var o=0;o<13;++o){
						document.write(s[o%4][0]);
						s[o%4].splice(0,1)
					}
				}
}
document.write('<input id="c"><button onclick=$()>Ok</button>');delete _
```

* 直接将 中间的代码另存为html，打开就是flag
``` 
<script>var t=["fl","s_a","i","e}"];
					var n=["a","_h0l","n"];
					var r=["g{","e","_0"];
					var i=["it'","_","n"];
					var s=[t,n,r,i];
					for(var o=0;o<13;++o){
						document.write(s[o%4][0]);
						s[o%4].splice(0,1)
					}
</script>
```
