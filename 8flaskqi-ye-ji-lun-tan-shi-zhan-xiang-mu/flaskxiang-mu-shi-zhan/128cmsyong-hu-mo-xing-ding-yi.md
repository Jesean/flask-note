### models.py

```
from exts import db
from datetime import datetime
# 加密函数, generate_password_hash哈希,check_password_hash检测密码是否一致
from werkzeug.security import  generate_password_hash,check_password_hash

# 创建cms用户数据库模型
class CMSUser(db.Model):
    # 设置表名
    __tablename__ = 'cms_user'
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    username = db.Column(db.String(50),nullable=False)
    _password = db.Column(db.String(100),nullable=False)
    email = db.Column(db.String(50),nullable=False,unique=True)
    join_time = db.Column(db.DateTime,default=datetime.now)

    def __init__(self,username,password,email):
        self.username = username
        self.password = password
        self.email = email

    # getter/setter
    # 可以将一个方法定义成属性
    @property
    def password(self):
        return self._password

    # 重新定义设置方法
    @password.setter
    def password(self,raw_password):
        # 加密
        self._password = generate_password_hash(raw_password)

    def check_password(self,raw_password):
        # 原始密码和加密后的密码是否一致
        result = check_password_hash(self._password,raw_password)
        return result

# 重写密码字段
# 密码:对外的字段名叫做password
#      对内的字段名叫做"_password"
```

### manage.py

```
#coding:utf-8

from flask_script import Manager
from flask_migrate import MigrateCommand,Migrate
from zlbbs import create_app
from exts import db
# 导入模型
from apps.cms import models

# 执行命令
# python manage.py db init:初始化
# python manage.py db migrate:执行迁移脚本
# 有可能报AttributeError: 'NoneType' object has no attribute 'encoding'的错误,是因为写数据库连接的时候,utf8写成了utf-8
# python manage.py db upgrade:映射到数据库中

app = create_app()

# 初始化app
manager = Manager(app)

# 绑定
Migrate(app,db)
# 映射
manager.add_command('db',MigrateCommand)

# 添加cms用户
@manager.option('-u','--username',dest='username')
@manager.option('-p','--password',dest='password')
@manager.option('-e','--email',dest='email')
def create_cms_user(username,password,email):
    user = models.CMSUser(username=username,password=password,email=email)
    db.session.add(user)
    db.session.commit()
    print("cms用户添加成功")
# 添加数据
# python manage.py create_cms_user -u miku -p 123456 -e 1479852727@qq.com

if __name__ == "__main__":
    manager.run()
```

### config.py

```
DEBUG = True

# 配置数据信息
DB_USERNAME = 'root'
DB_PASSWORD = '123456'
DB_HOST = '127.0.0.1'
DB_PORT = '3306'
DB_NAME = 'zlbbs'
DB_URI = 'mysql+pymysql://{}:{}@{}:{}/{}?charset=utf8'.format(DB_USERNAME,DB_PASSWORD,DB_HOST,DB_PORT,DB_NAME)

# 数据库
SQLALCHEMY_DATABASE_URI = DB_URI
# 屏蔽SQLalchemy发送的信号
SQLALCHEMY_TRACK_MODIFICATIONS = False
```



