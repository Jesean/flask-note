Ajax的crsf保护实现

以login.html为例

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>中国工商银行登录界面</title>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="{{ url_for('static',filename='login.js') }}"></script>
</head>
<body>
    <form action="" method="post">
{#        {{ form.csrf_token }}#}
        <input type="hidden" name="csrf_token" value="{{ csrf_token() }}" />
        <table>
            <tbody>
                <tr>
                    <td>邮箱:</td>
                    <td><input type="text" name="email"/></td>
                </tr>
                <tr>
                    <td>密码:</td>
                    <td><input type="password" name="password"/></td>
                </tr>
                <tr>
                    <td></td>
                    <td><input type="submit" valule="登录" id="submit"/></td>
                </tr>
            </tbody>
        </table>
    </form>
</body>
</html>
```

login.js

```
// jquery
// XMLHTTTPRequest

// 整个文档都加载完毕后才会执行这个函数
$(function () {
    $('#submit').click(function (event) {
        // 阻止默认的提交表单的行为
        event.preventDefault();
        var email = $('input[name=email]').val();
        var password = $('input[name=password]').val();
        var csrf_token = $('input[name=csrf_token]').val()
        $.post({
            'url': '/login/',
            'data': {
                'email': email,
                'password': password,
                'csrf_token':csrf_token
            },
            'success': function (data) {
                console.log("成功");
            },
            'fail': function (error) {
                console.log(error);
            }
        });
    });
});
```



