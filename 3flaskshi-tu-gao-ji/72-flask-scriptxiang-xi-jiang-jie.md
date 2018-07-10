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
    'hello world'
    def run(self):
        print('hello world')

#自定义命令一：
manager.add_command('hello', Hello())
# 自定义命令二：
manager.add_command("runserver", Server()) #命令是runserver
if __name__ == '__main__':  
    manager.run()  
```



```

```



