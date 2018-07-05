### limit、offset和切片

1. limit:可以限制每次查询的时候只查询几条数据。
   1. ```
      获取前10条数据
      articles = session.query(Article).limit(10).all()
      ```
2. offset:可以限制查找数据的时候过来前面多少条。
3. 切片:可以Query对象使用切片操作，来获取想要的数据





