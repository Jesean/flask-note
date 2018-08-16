### 1.自定义404页面

```
{% from 'common/_macros.html' import static %}
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
    <title>该页面不存在喔</title>
    <meta name="keywords" content="" />
    <meta name="description" content="" />
	<link rel="stylesheet" href="{{ static('front/css/404.css') }}"/>
</head>
<body>
<div class="error wp960 auto">
    <div class="img">
        <img src="{{ url_for('static',filename='common/images/error.jpg') }}" />
    </div>
    <div><a class="back" href="/">返回首页</a></div>
</div>
</body>
</html>

```

### 2.自定义404视图

```
@app.errorhandler(404)
def page_not_found(e):
    return render_template('front/404.html'), 404
```

### 3.帖子详情页面

```
@bp.route('/p/<post_id>/')
def post_detail(post_id):
    post = PostModel.query.get(post_id)
    if not post:
        abort(404)
    return render_template('front/pdetail.html',post=post)
```



