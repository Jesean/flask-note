### 1.定义模型

```
from exts import  db
from datetime import datetime

class BannersModel(db.Model):
    __tablename__ = "banners_model"
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    name = db.Column(db.String(255),nullable=False)
    image_url = db.Column(db.String(255),nullable=False)
    link_url = db.Column(db.String(255),nullable=False)
    priority = db.Column(db.Integer,default=0)
    create_time = db.Column(db.DateTime,default=datetime.now)

```

### 2.映射到数据库中

```
from apps import models as apps_models
```

```
python manage.py db migrate
python manage.py db upgrade
```



