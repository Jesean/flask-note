### 蓝图中静态文件的查找规则

* 默认会在项目的static文件夹下查找文件

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>新闻列表</title>
    <link rel="stylesheet" href="{{ url_for('static',filename='news.css')}}">
</head>
<body>
    <p style="background-color: pink;">这是从模板中渲染的代码</p>
</body>
</html>
```





