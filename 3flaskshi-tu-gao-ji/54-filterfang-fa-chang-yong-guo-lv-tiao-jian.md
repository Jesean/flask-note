## 过滤条件

过滤是数据库的一个很重要的功能，以下对一些常用的过滤条件进行解释，并且这些过滤条件都是只能通过filter方法实现的

1.equals

```
article = session.query(Article).filter(Article.id == 1).first()
print(article)
```

2.not equals

```
article = session.query(Article).filter(Article.title != 'title0').all()
print(article)
```

3.like & ilike\(不区分大小写\)

```
rticles = session.query(Article).filter(Article.title.like('%title%')).all()
# 不分区大小写
articles = session.query(Article).filter(Article.title.ilike('%title%')).all()
print(articles)
```

4.in

```
articles = session.query(Article).filter(Article.title.in_(['title1','title2'])).all()
print(articles)
```

5.not in

```
icles = session.query(Article).filter(~Article.title.in_(['title1'])).all()
# articles = session.query(Article).filter(Article.title.notin_(['title1'])).all()
print(articles)
```

6.is null

```
session.query(Article).filter(Article.content == None).all()
print(articles)
```

7.is not null

```
articles = session.query(Article).filter(Article.content != None).all()
print(articles)
```

8.or

```
articles = session.query(Article).filter(or_(Article.title=='title0',Article.content=='123')).all()
print(articles)
```

9.and

```
rticles = session.query(Article).filter(Article.title=='title0' and Article.content == '123').all()
articles = session.query(Article).filter(and_(Article.title=='title0',Article.content == '123')).all()
print(articles)
```



