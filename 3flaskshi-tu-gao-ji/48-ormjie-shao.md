### 将ORM模型映射到数据库中

* 用“declarative\_base”根据"engine"创建一个ORM基类

```
from sqlalchemy.ext.declarative import declarative_base

engine = create_engine(DB_URI)

Base = declarative_base(engine)
```

* 用这个"Base"类作为基类来写自己的ORM类。要定义"\_\__tablename_\_\_"类属性，来指定这个模型映射到数据库中的表名

```
class Person(Base):
    __tablename__ = "person"
    ...
```

* 创建需要在表中映射的字段，所有需要映射到表中的属性都应为Column类型

```
class Person(Base):
    __tablename__ = "person"
    # 2.要在这个ORM模型中创建一些属性，来跟表中的字段进行一一映射。这些属性必须是SQLAlchemy给我们提供好的数据类型
    # Column()对象
    id = Column(Integer,primary_key=True,autoincrement=True)
    # String(50)==>varchar(50)
    name = Column(String(50))
    age = Column(Integer)
```



