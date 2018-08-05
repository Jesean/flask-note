邮箱界面resetemail.html

```
{% extends 'cms/base.html' %}

{% block title -%}
    修改邮箱
{%- endblock %}

{% block head %}
    <style>
        .form-container{
            width:300px;
        }
    </style>
{% endblock %}

{% block page_title %}
    {{ self.title() }}
{% endblock %}

{% block main_content %}
    <form action="" method="post">
        <div class="form-container">
            <div class="form-group">
                <div class="input-group">
                    <input type="email" class="form-control" name="email" placeholder="新邮箱">
                    <span class="input-group-addon">获取验证码</span>
                </div>
            </div>
            <div class="form-group">
                <input type="text" class="form-control" placeholder="邮箱验证码">
            </div>
            <div class="form-group">
                <button class="btn btn-primary">立即修改</button>
            </div>
        </div>
    </form>
{% endblock %}
```



