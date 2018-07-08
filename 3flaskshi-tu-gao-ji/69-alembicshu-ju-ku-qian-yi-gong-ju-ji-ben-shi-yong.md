### alembic教程

alembic是sqlalchemy的作者开发的。用来做ORM模型与数据的迁移与映射。alembic使用方式跟git有点类似，表现在两个方面，第一个，alembic的所有命令都是以alembic开头，第二，alembic的迁移文件也是通过版本进行控制的。首先，通过pip install alembic进行安装。以下将解释alembic的用法:

1.初始化alembic仓库:在终端中，cd到项目目录中，然后执行alembic init alembic，创建一个名叫alembic的仓库。

2.创建模型类:创建一个models.py模块，然后在里面定义模型类，示例代码:

```
from sqlalchemy import create_engine,Column,String,Float,Integer
from sqlalchemy.ext.declarative import declarative_base
# from sqlalchemy.orm import sessionmaker

HOSTNAME = "127.0.0.1"
PORT = "3306"
DATABASE = "alembic_demo"
USERNAME = "root"
PASSWORD = "123456"
# dialect+dricer://username:password@host:port/database
DB_URI = "mysql+pymysql://{}:{}@{}:{}/{}?charset=utf8".format(USERNAME,PASSWORD,HOSTNAME,PORT,DATABASE)

engine = create_engine(engine)
Base = declarative_base(engine)
# session = sessionmaker(engine)()

class User(Base):
    __tablename__ = "user"
    id = Column(Integer,primary_key=True,autoincrement=True)
    username = Column(String(50),nullable=False)
```

3.修改配置文件:

* 在alembic.ini中设置数据库的连接，sqlalchemy.url = driver://user:pass@localhost/dbname，比较以mysql数据库为例，则配置后的代码为:
* ```
  sqlalchemy.url = mysql+pymysql://root:123456@localhost/alembic_demo?charset=utf8
  ```
* 为了使用模型类更新数据库，需要在env.py文件中设置target\_metadata_，_默认为target



