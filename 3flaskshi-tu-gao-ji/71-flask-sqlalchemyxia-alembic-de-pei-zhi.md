### myapp.py

```
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
import config

app = Flask(__name__)
app.config.from_object(config)
db = SQLAlchemy(app)

# alembic revision --autogenerate -m "第一次提交"
# alembic upgrade head

# alembic revision --autogenerate -m "add age column"
# alembic upgrade head
class User(db.Model):
    __tablename__ = "user"
    id = db.Column(db.Integer,primary_key=True,autoincrement=True)
    username = db.Column(db.String(50),nullable=False)
    age = db.Column(db.Integer)

@app.route('/')
def hello_world():
    return 'Hello World!'


if __name__ == '__main__':
    app.run(debug=True)

```



