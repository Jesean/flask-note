## Flask-WTF

Flask-WTF是简化了WTForms操作的一个第三方库，WTForms表单的两个主要功能是验证用户提交数据的合法性以及渲染模板。当然还包括一些其他的功能:_CSRF保护_，文件上传等，安装Flask-WTF默认也会安装WTForms。

### 安装

```
pip install flask-wtf
```

## 表单验证

#### myapp.py

```
from flask import Flask,request,render_template
from wtforms import Form,StringField
from wtforms.validators import Length,EqualTo

# 继承Form
class RegistForm(Form):
    # message指定错误信息
    username = StringField(validators=[Length(min=3,max=10,message="用户名长度必须在3到10位之间")])
    password = StringField(validators=[Length(min=6,max=10)])
    # EqualTo指定与之保持相同值的字段
    password_repeat = StringField(validators=[Length(min=6,max=10),EqualTo("password")])

app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'

@app.route("/regist/",methods=["GET","POST"])
def regist():
    if request.method == "GET":
        return render_template("regist.html")
    else:
        form = RegistForm(request.form)
        if form.validate():
            return "success"
        else:
            # 打印失败原因
            print(form.errors)
            return "fail"

if __name__ == '__main__':
    app.run(debug=True)

```



