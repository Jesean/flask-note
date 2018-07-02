### 将ORM模型映射到数据库中

* 用“declarative\_base”根据"engine"创建一个ORM基类

```
from sqlalchemy.ext.declarative import declarative_base

engine = create_engine(DB_URI)

Base = declarative_base(engine)
```

* 用这个"Base"类作为基类来写自己的ORM类。要定义"\_\__tablename_\_\_"



