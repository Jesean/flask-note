## 静态文件

1. 加载静态文件使用的是"urf\_for"函数u，然后第一个参数需要为"static",第二个参数需要为"filename='路径' "，示例:
2. ```
   {{ ur_for('static',filename="css/xxx.css") }}

   格式:
   {{ url_for('static',filename="在static下的相对路径") }}
   ```

```
app.py

from flask import Flask, render_template

app = Flask(__name__)
app.config.update({
    'DEBUG':True,
    "TEMPLATES_AUTO_RELOAD":True,
})

@app.route('/')
def hello_world():
    return render_template("index.html")


if __name__ == '__main__':
    # app.run(debug=True)
    app.run(host="0.0.0.0")
```



