### 基于方法的类视图

1. 基于方法

```
class LoginView(views.MethodView):
    def get(self):
        return render_template('login.html')

    def post(self):
        username = request.form.get('name')
        password = request.form.get('password')
        if username == 'angle' and password == '123456':
            return '成功'
        else:
            return "失败"

app.add_url_rule(rule='/login/',view_func=LoginView.as_view('login'))
```

![](/assets/39.1.png)

```
class LoginView(views.MethodView):

"""
    def __render(self,error=None):
        return render_template('login.html', error=error)

    # get请求执行这个代码
    def get(self):
        return self.__render()
"""

    # get请求执行这个代码
    def get(self,error=None):
        return render_template('login.html',error=error)

    # post请求执行这个代码
    def post(self):
        username = request.form.get('name')
        password = request.form.get('password')
        if username == 'angle' and password == '123456':
            return '成功'
        else:
            # return render_template('login.html',error='用户名/密码错误')
            return self.get(error='用户名/密码错误')

app.add_url_rule(rule='/login/',view_func=LoginView.as_view('login'))
```

![](/assets/39.3.png)

