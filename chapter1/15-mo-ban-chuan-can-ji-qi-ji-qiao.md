## 模板-参数

1. 在使用
2. 
```
from flask import Flask, Response, jsonify, render_template

app = Flask(__name__)

@app.route("/")
def hell0_world():

    context = {
        "username":"miku",
        "age":18,
        "contry":"china",
        "childrens":{
            "name":"abc",
            "height":180,
        }
    }

    return render_template("index.html",**context)

if __name__ == '__main__':
    app.run(debug=True)
```

![](file:///C:\Users\miku\AppData\Roaming\Tencent\Users\1479852727\QQ\WinTemp\RichOle\3MD6G{BO5O~QID%29[OAKE_X7.png)

