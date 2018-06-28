```
url_for 笔记

模板中的'url_for'跟后台视图函数中的'urf_for'使用起来基本一模一样的，
也是传递视图函数的名字，也可以传递参数，需要在'url_for'左右两边加上一个{{}}
```

```
from flask import Flask, render_template, url_for

app = Flask(__name__)

@app.route("/")
def hello_world():
    return render_template("index.html")

@app.route('/acounts/login/<id>/')
def login(id):
    # print(id)
    return render_template('login.html')

if __name__ == '__main__':
    app.run(debug=True)

```



