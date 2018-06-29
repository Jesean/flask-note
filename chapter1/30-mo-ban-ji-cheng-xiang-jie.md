## 模板继承笔记

### 为什么需要继承模板:

模板继承可以把一些公用的代码单独抽取出来放到一个父模板中，以后子模板直接就可以使用了。这样可以重复性的代码，以后修改起来比较方便

### 模板继承语法:

使用"extends"语句，来指明继承的父模板，父模板的路径，也是相对于'templates'文件夹下的绝对路径。示例代码如下:

```
{% extends "base.html" %}
```

### block语法

在父模板中，只能定义一些公共的代码。子模板可能要根据具体的需要实现不同的代码，这时候父模板就应该有能力提供一个借口，让父模板来实现，从而实现具体业务需求的功能。

在父模板中:

```
{% block block的名字 %}
{% endblock %}
```

在子模板中

```
{% block block的名字 %}
子模板的代码
{% endblock%}
```

### 调用父模板代码block中的代码

默认情况下，子模板如果实现了父模板定义的block，那么子模板block中的代码就会覆盖掉父模板的代码。如果想要在子模板中仍然保持父模板中的代码，那么可以使用""来实现。

```
{% block body_block %}

<p style="background-color:red;">
这是父模板的代码
</p>
{% endblock %}


{% extends "base.html"%}
{% block body_block %}
{{super()}}
<p style="background:pink;">我是子模板中的代码</p>
{% endblock %}
```



