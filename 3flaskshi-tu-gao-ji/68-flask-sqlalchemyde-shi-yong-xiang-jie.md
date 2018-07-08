## Flask-SQLAlchemy

### 安装

```
pip install  flask-sqlalchemy
```

### 数据库连接

```
1.定义数据库连接字符串DB_URI
2.将定义好的数据库连接字符串DB_URI放到配置文件中
app.config["SQLALCHEMY_DATABASE_URI"] = DB_URI
3.使用"flask_sqlalchemy.SQLAlchemy"类定义一个对象，并将"app"传入进去
db = SQLAlchemy(app)
```

### 创建ORM模型

```
1.定义模型，不使用"delarative_base"来创建一个基类，而是使用"db.Model"来作为基类
2.在模型类中，'Column'、'String'、'Integer'以及'relationship'等，直接使用db.xxx调用
"db.Column()"
3.在定义模型的时候，可以不写"__tablename__"，那么"flask_sqlalchemy"会默认使用当前的模型的名字转换成小写作为表的名字，
并且如果这个模型的名字使用了多个单词并且使用了驼峰命名法，那么会在多个单词之间会使用下划线进行连接。
'''
# user_model
class UserModel(db.Model)
    ....
'''
```

### 将ORM模型映射到数据库

### 使用session

### 查询数据



