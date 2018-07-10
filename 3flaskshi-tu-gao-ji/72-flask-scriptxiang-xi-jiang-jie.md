## Flask-Script:

Flask-Script的作用是可以通过命令行的形式来操作Flask。

### 安装

```
pip install flask-script
```

### 三种创建命令:使用@command修饰符、使用@option修饰符、创建command子类

#### @command修饰符

```
from flask_script import Manager
from myapp import app,BackendUser,db
from db_script import db_manager

# 使用Manager创建一个对象
manager = Manager(app)

@manager.command
def greet():
    print("你好")

if __name__ == '__main__':
    manager.run()
```

命令:python manage.py greet

#### @option修饰符

添加参数

```
from flask_script import Manager
from myapp import app,BackendUser,db
from db_script import db_manager

# 使用Manager创建一个对象
manager = Manager(app)

@manager.option("-u","--username",dest="username")
@manager.option("-a","--age",dest="age")
def add_user(username,age):
     print("用户名:{},年龄:{}".format(username,age))


if __name__ == '__main__':
    manager.run()
```

命令: python manage.py add\_user  -u angle -a 18

tips:可以有多个@option选项参数，命令即可使用-u，又可使用--username，dest指定用户输入命令时将值作为参数传给了函数中的username。

#### command子类

```
from flask_script import Manager  ，Server
from flask_script import Command  
from debug import app  

manager = Manager(app)  

class Hello(Command):
    def run(self):
        print('测试')

#自定义命令一/将类Hello()映射为hello
manager.add_command('hello', Hello())

#自定义命令二/启动命令
manager.add_command("runserver", Server()) #命令是runserver
if __name__ == '__main__':
    manager.run()
```

#### 子类

db\_script.py

```
from flask_script import  Manager

db_manager = Manager()

@db_manager.command
def init():
    print('迁移仓库创建完毕')

@db_manager.command
def revision():
    print("迁移脚本生成成功")

@db_manager.command
def upgrade():
    print("脚本映射到数据库成功")
```

manage.py

```
from flask_script import Manager
from myapp import app,BackendUser,db
from db_script import db_manager

# 使用Manager创建一个对象
manager = Manager(app)

# 添加子命令
# python manage.py db init
manager.add_command("db",db_manager)

@manager.option("-u","--username",dest="username")
@manager.option("-e","--email",dest="email")
def add_user(username,email):
    user = BackendUser(username=username,email=email)
    db.session.add(user)
    db.session.commit()
    
if __name__ == '__main__':
    manager.run()
```

myapp.py

```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
import config

app = Flask(__name__)
app.config.from_object(config)

db = SQLAlchemy(app)

class BackendUser(db.Model):
    __tablename__ = "backend_user"
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    username = db.Column(db.String(50),nullable=False)
    email = db.Column(db.String(50),nullable=False)

# 可以使用alembic
db.drop_all()
db.create_all()

@app.route('/')
def hello_world():
    return 'Hello World!'


if __name__ == '__main__':
    app.run()

```



