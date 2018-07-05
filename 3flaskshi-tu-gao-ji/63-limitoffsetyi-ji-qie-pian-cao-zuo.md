### limit、offset和切片

1. limit:可以限制每次查询的时候只查询几条数据。
   1. ```
      获取前10条数据
      articles = session.query(Article).limit(10).all()
      ```
2. offset:可以限制查找数据的时候过来前面多少条。
   1. ```
      # select * from article limit 4 offset 9
      # select * from article limit 9,4
      # articles = session.query(Article).order_by(Article.id.desc()).offset(10).limit(10).all()
      # slice(limit,offset),desc()降序
      # articles = session.query(Article).order_by(Article.id.desc()).slice(0,10).all()
      ```
3. 切片:可以Query对象使用切片操作，来获取想要的数据



