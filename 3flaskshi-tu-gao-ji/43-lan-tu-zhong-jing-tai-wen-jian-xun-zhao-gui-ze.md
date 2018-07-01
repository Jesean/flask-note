### 蓝图中静态文件的查找规则

* 在模板文件中，加载静态文件，如果使用url\_for\('static'\)，只会在app模板文件夹目录下查找静态文件
* 如果在加载静态文件的时候，指定的蓝图的名字，比如:'news.static',那么就会到这个蓝图指定的static\_forder下查找静态文件

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>新闻列表</title>
      <link rel="stylesheet" href="{{ url_for('news.static',filename='news.css')}}">
</head>
<body>
    <p style="background-color: pink;">这是从模板中渲染的代码</p>
</body>
</html>
```



