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

### 将ORM模型映射到数据库

### 使用session

### 查询数据



