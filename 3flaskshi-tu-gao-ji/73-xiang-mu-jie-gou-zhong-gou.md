#### exts.py

```
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()
```

#### models.py

```
from exts import db

class User(db.Model):
    __tablename__ = "user"
    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    username = db.Column(db.String(50), nullable=False)

```

#### config.py

```
HOSTNAME = "127.0.0.1"
PORT = "3306"
DATABASE = "alembic_demo"
USERNAME = "root"
PASSWORD = "123456"
# dialect+dricer://username:password@host:port/database
DB_URI = "mysql+pymysql://{}:{}@{}:{}/{}?charset=utf8".format(USERNAME,PASSWORD,HOSTNAME,PORT,DATABASE)

SQLALCHEMY_DATABASE_URI = DB_URI
```

#### myapp.py

```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
import config
from exts import db

app = Flask(__name__)
app.config.from_object(config)
# 获取app
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



