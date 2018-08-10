抽离共同元素

```
{% from "common/_macros.html" import static %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="csrf-token" content="{{ csrf_token() }}">
    <title>{% block title %}{% endblock %}</title>
    <script src="http://cdn.bootcss.com/jquery/3.1.1/jquery.min.js"></script>
    <link href="http://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <script src="http://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <script src="http://cdn.bootcss.com/blueimp-md5/2.10.0/js/md5.min.js"></script>
    <script src="{{ static('common/zlparam.js') }}"></script>
     <script src="{{ static("common/zlajax.js") }}"></script>
     <link rel="stylesheet" href="{{ static("common/sweetalert/sweetalert.css") }}">
    <script src="{{ static("common/sweetalert/sweetalert.min.js") }}"></script>
    <script src="{{ static("common/sweetalert/zlalert.js") }}"></script>
    {% block head %}

    {% endblock %}
</head>
<body>
    <div class="outer-box">
        <div class="logo-box">
            <a href="/">
                <img src="{{ static("common/images/logo.png") }}"/>
            </a>
        </div>
        <h2 class="page-title">
            {% block h2_block %}{% endblock %}
        </h2>

        <div class="sign-box">
            {% block signbox %}
            
            {% endblock %}
        </div>
    </div>
</body>
</html>
```

注册页面

```
{% extends 'front/signbase.html' %}
{% from "common/_macros.html" import static %}

{% block title %}
    论坛注册
{% endblock %}

{% block head %}
    <script src="{{ static("front/js/signup.js") }}"></script>
    <link href="{{ static("front/css/signup.css") }}" rel="stylesheet">
{% endblock %}

{% block h2_block %}
    论坛账号登录
{% endblock %}

{% block signbox %}
    <div class="form-group">
                <div class="input-group">
                    <input type="text" name="telephone" class="form-control" placeholder="手机号码">
                    <span class="input-group-btn">
                        <button  id="sms-captcha-btn" class="btn btn-default">
                            发送验证码
                        </button>
                    </span>
                </div>
            </div>
            <div class="form-group">
                <input type="text" name="sms_captcha" class="form-control" placeholder="短信验证码">
            </div>
            <div class="form-group">
                <input type="text" name="username" class="form-control" placeholder="用户名">
            </div>
            <div class="form-group">
                <input type="password" name="password1" class="form-control" placeholder="密码">
            </div>
            <div class="form-group">
                <input type="password" name="password2" class="form-control" placeholder="确认密码">
            </div>
            <div class="form-group">
                <div class="input-group">
                    <input type="text" name="graph_captcha" class="form-control" placeholder="图形验证码">
                    <span class="input-group-addon captcha-addon">
                <img id="captcha-img" class="captcha-img" src="{{ url_for('common.graph_captcha') }}" alt="">
                    </span>
                </div>
            </div>
            <div class="form-group">
                <span style="display: none;" id="return-to-span">{{ return_to }}</span>
                <button id="submit-btn" class="btn btn-warning btn-block">
                    立即注册
                </button>
            </div>
{% endblock %}
```



