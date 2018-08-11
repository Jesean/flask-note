### 1.相关链接

组件:

### 2.抽离模板

```
<meta name="csrf-token" content="{{ csrf_token() }}">
<script src="http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js"></script>
<link href="http://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
<script src="http://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<script src="{{ url_for('static',filename="common/zlajax.js") }}"></script>
<link rel="stylesheet" href="{{ url_for('static',filename="common/sweetalert/sweetalert.css") }}">
<script src="{{ url_for('static',filename="common/sweetalert/sweetalert.min.js") }}"></script>
<script src="{{ url_for('static',filename="common/sweetalert/zlalert.js") }}"></script>
```

### 3.首页模板

```
{% extends "front/base.html" %}

{% block title %}
    Tokimeki论坛
{% endblock %}


{% block head %}

{% endblock %}


{% block body %}
    {{ self.title() }}
{% endblock %}
```



