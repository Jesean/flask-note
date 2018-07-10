#### exts.py

```
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()
```

#### models.py

```
from exts import db

class User(db.Model):
    __tablename__ = 'user'
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    username = db.Column(db.String(50),nullable=False)
```

#### config.py

```
DB_USERNAME = 'root'
DB_PASSWORD = '123456'
DB_HOST = '127.0.0.1'
DB_PORT = '3306'
DB_NAME = 'flask_migrate_demo'

DB_URI = 'mysql+pymysql://%s:%s@%s:%s/%s?charset=utf8' % (DB_USERNAME,DB_PASSWORD,DB_HOST,DB_PORT,DB_NAME)

SQLALCHEMY_DATABASE_URI = DB_URI
```

#### myapp.py

```
from flask import Flask
import config
from exts import db

app = Flask(__name__)
app.config.from_object(config)
db.init_app(app)


@app.route('/')
def hello_world():
    return 'Hello World!'

@app.route("/profile/")
def profile():
    pass


if __name__ == '__main__':
    app.run()

```



