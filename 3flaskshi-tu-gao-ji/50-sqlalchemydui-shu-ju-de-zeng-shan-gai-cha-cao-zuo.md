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

