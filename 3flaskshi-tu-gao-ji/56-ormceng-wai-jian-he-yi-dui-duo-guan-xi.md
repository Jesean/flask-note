### ORM关系以及一对多

mysql级别的外键，还不够ORM，必须拿到一个表中的外键，然后再去通过这个外键再去另外一张表查找

```
# 表之间的关系
article = session.query(Article).first()
uid = article.uid
print(article)
# get方法只匹配主键字段
user = session.query(User).get(uid)
print(user)
print(uid)
```

可这样太麻烦了。SQLAlchemy提供了一个"relationship"，这个类可以定义属性，以后再访问相关联的表的时候就可以直接通过属性访问的方式就可以访问得到了。

```
class User(Base):
    ....
    articles = relationship('Article')

    def __repr__(self):
        return "<User(username:%s)>" % self.username

class Article(Base):
    ....
    # 映射到User模型
    # backref:反向引用,为user添加一个属性
    author = relationship("User")

    def __repr__(self):
        return "<Article(title:%s),content:%s>" % (self.title,self.content)



article = session.query(Article).first()
print(article.author.username)

user = session.query(User).first()
print(user.articles)
```



