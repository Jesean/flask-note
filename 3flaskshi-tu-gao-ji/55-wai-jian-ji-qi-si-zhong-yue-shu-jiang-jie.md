### 外键

在MySQL中，外键可以让表之间的关系更加紧密，而SQLAlchemy同样支持外键。通过FpreignKey类来实现，并且可以指定表的外键约束。相关示例代码如下:

```
from sqlalchemy import create_engine, Column, Integer, Text, String, 
DateTime, String, Float, func,and_,or_,ForeignKey

class User(Base):
    __tablename__ = 'user'
    id = Column(Integer,primary_key=True,autoincrement=True)
    username = Column(String(50),nullable=False)

class Article(Base):
    __tablename__ = "article"
    id = Column(Integer,primary_key=True,autoincrement=True)
    title = Column(String(50),nullable=False)
    content = Column(Text,nullable=False)

    # 外键
    uid = Column(Integer,ForeignKey("user.id"))

Base.metadata.drop_all()
Base.metadata.create_all()
```

外键约束有以下几项:

1. RESTRICT\(restrict\):父表数据被删除，会阻止删除
2. NO ACTION:在MySQL中，同RESTRICT
3. CASCADE:级联删除
4. SET NULL:父类数据被删除，子表数据会跟着删除



