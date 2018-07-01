## 蓝图实现子域名

* 使用蓝图技术

* 在创建蓝图对象的时候，需要传递一个"subdomain"参数,来指定这个子域名的前缀，例如

```
from flask import Blueprint

cms_bp = Blueprint('cms',__name__,subdomain='cms')

@cms_bp.route('/')
def index():
    return "cms index page"
```

1. 需要在主app文件中，需要配置app.config的SERVER\_NAME参数，例如:

```
from flask import Flask,Blueprint,url_for,render_template

from blueprints.news import news_bp
from blueprints.user import user_bp
from blueprints.cms import cms_bp

# Blueprint蓝图:将大型flask项目模块化

app = Flask(__name__)
app.config['SERVER_NAME'] = 'jd.com:5000'

# 注册一个蓝图
app.register_blueprint(user_bp)
app.register_blueprint(news_bp)
app.register_blueprint(cms_bp)

# 用户模块
# 新闻模块
# 电影模块
# 读书模块

# ip地址、localhost不能有子域名
# cms:127.0.0.1:5000和localhost不能访问

@app.route('/')
def hello_world():
    # url_for('指定蓝图名字.视图函数名字')
    print(url_for('news.news_list'))
    # return 'Hello World!'
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```



