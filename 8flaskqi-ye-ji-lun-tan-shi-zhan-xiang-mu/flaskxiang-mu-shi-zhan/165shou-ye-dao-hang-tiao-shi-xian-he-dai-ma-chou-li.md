### 1.相关链接

组件:

### 2.抽离模板

```
<meta name="csrf-token" content="{{ csrf_token() }}">
<script src="http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js"></script>
<link href="http://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
<script src="http://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
<script src="{{ static("common/zlajax.js") }}"></script>
<link rel="stylesheet" href="{{ static("common/sweetalert/sweetalert.css") }}">
<script src="{{ static("common/sweetalert/sweetalert.min.js") }}"></script>
<script src="{{ static("common/sweetalert/zlalert.js") }}"></script>
```

### 3.首页模板

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    {% include "common/_heads.html" %}
    <title>
        {% block title %}{% endblock %}
    </title>
    {% block head %}{% endblock %}
</head>
<body>

</body>
</html>
```



