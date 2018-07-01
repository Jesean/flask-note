```
from flask import Flask,request
from functools import wraps

app = Flask(__name__)

def login_required(func):
    @wraps(func)
    def wrapper(*args,**kwargs):
        # 获取参数
        # login?username=xxx
        username  = request.args.get("username")
        if username and username == "angle":
            return func(*args,**kwargs)
        else:
            return "请先登录"
    return wrapper


@app.route('/')
def hello_world():
    return 'Hello World!'

@app.route('/settings/')
@login_required
def settings():
    return "这是设置界面"

if __name__ == '__main__':
    app.run(debug=True)
```

![](/assets/40.login_required.png)![](/assets/40.login.png)

```
class ProfileView(views.View):

    # 装饰器
    decorators = [login_required]

    def dispatch_request(self):
        return "个人中心界面"

app.add_url_rule(rule='/profile/',view_func=ProfileView.as_view('profile'))

```



