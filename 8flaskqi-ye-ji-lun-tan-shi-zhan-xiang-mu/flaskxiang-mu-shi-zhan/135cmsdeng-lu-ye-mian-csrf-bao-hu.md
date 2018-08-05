### 开启crsf保护

```
from flask_wtf.csrf import CSRFProtect
....
CSRFProtect(app)

在表单中添加如下:
<input type="hidden" name="csrf_token" value="{{ csrf_token() }}" />


# 可以惰性加载
crsf = CSRFProtect()
crsf.init_app(app)
```

无论何时为通过csrf验证都会返回响应，可以定义这个错误响应

```
@crsf.error_handler
def csrf_error(reason):
    return render_template("xx.html",reason=reason),400
```

提供某些视图不需要保护

```
@csrf.exempt
@app.route('/foo', methods=('GET', 'POST'))
def my_handler():
    # ...
    return 'ok'
```

默认情况下你也可以在所有的视图中禁用 CSRF 保护，通过设置`WTF_CSRF_CHECK_DEFAULT`为`False`，仅仅当你需要的时候选择调用`csrf.protect()`。这也能够让你在检查 CSRF 令牌前做一些预先处理:

```
@app.before_request
def check_csrf():
    if not is_oauth(request):
        csrf.protect()
```



