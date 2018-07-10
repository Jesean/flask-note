## Flask-Migrate

在实际的开发环境中，经常会发生数据库修改的行为。一般修改数据库不会直接手动的去修改，而是去修改ORM对应的模型，然后再把模型映射到数据库中。

flask-migrate是基于Alembic的一个封装，并继承了到Flask中，而所有的迁移操作其实都是Alembic操作的，能够跟踪模型的变化，并将变化映射到数据库中。

#### 安装命令

```
pip install flask-migrate
```

#### 配置flask-migrate

```
from flask_script import Manager
from myapp import app
from flask_migrate import Migrate,MigrateCommand
from exts import db

manager = Manager(app)
Migrate(app,db)
manager.add_command("db",MigrateCommand)
```

##### 使用init命令创建迁移仓库

```
python manage.py db init
```

#### 使用migrate命令将模型映射到文件中

```
python manage.py db migrate
# python manage.py db migrate -m "initial migratetion"
```

#### 使用upgrade命令将文件数据映射到数据库中

```
python manage.py db upgrade
```

#### 使用downgrade命令回滚迁移中的数据库改动、

```
python manage.py db downgrade version(上一个版本的版本号)
```



