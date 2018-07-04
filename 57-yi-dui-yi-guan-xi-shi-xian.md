### 一对一的关系

在sqlalchemy中，如果想要将两个模型映射程一对一的关系，name应该在父模型中，指定引用的时候，要传递一个"uselist=False"这个参数进去，就是告诉父模型，以后引用这个从模型的时候，不再是一个列表了，而是一个对象。示例代码如下:

```
class User(Base):
    __tablename__ = 'user'
    id = Column(Integer,primary_key=True,autoincrement=True)
    username = Column(String(50))

    # uselist:指定返回的数据不是列表，只是一个属性
    extend = relationship("UserExtend",uselist=False)

    def __repr__(self):
        return "<User(username:%s)>" % self.username

class UserExtend(Base):
    __tablename__ = "user_extend"
    id = Column(Integer,primary_key=True,autoincrement=True)
    school = Column(String(50))
    uid = Column(Integer,ForeignKey('user.id'))

    user = relationship('User',backref='extend')
```

当然，也可以借助"sqlchemy.orm.backref"来简化代码:

```
class User(Base):
    __tablename__ = 'user'
    id = Column(Integer,primary_key=True,autoincrement=True)
    username = Column(String(50))

    def __repr__(self):
        return "<User(username:%s)>" % self.username

class UserExtend(Base):
    __tablename__ = "user_extend"
    id = Column(Integer,primary_key=True,autoincrement=True)
    school = Column(String(50))
    uid = Column(Integer,ForeignKey('user.id'))

    user = relationship('User',backref=backref('extend',uselist=False))

```



