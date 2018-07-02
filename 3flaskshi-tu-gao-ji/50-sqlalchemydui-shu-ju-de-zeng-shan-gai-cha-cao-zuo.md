### 用session做数据的增删查改操作

1.构建session对象，所有和数据库的ORM操作必须通过一个叫做"session"的会话对象来实现，通过以下代码来获取会话对象:

```
from sqlalchemy.orm import sessionmaker

# Session = sessionmaker(engine)
# session = Session()
# 上面两行等价于下面一行
session = sessionmaker(engine)()
```

2.添加对象

* 创建对象，也即创建一条数据

```
p = Person(name="angle",age=16,country="china")
```

* 将对象添加到'session'会话对象中

```
session.add(p)
```

* 将session中的对象做commit操作\(提交\)

```
session.commit()
```

* 一次性添加多条数据

```
p1 = Person(name="angle1",age=16,country="china")
p2 = Person(name='angle2',age=20,country='china')
session.add_all([p1,p2])
```

3.查改对象

```
#查找某个模型对应的那个表中所有的数据:
all_person = session.query(Person).all()

# 使用filter_by来做条件查询
all_person = session.query(Person).filter_by(name='angle1').all()

# 使用filter来做条件查询
all_person = session.query(Person).filter(Person.name.contains('angle'))

#使用get方法查找数据，get方法是根据id来查询的，只会返回一条数据或者None
person = session.query(Person).get(primary_key)

#使用first方法获取结果集中的第一条数据
person = session.query(Person).first()
```

4.修改对象,首先在数据库查找数据，然后将数据进行修改，最后做commit操作

```
person = session.query(Person).first()
person.name = 'angle_update'
session.commit()
```

5.删除对象

