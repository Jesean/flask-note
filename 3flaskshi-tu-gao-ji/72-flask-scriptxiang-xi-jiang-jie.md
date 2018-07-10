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

