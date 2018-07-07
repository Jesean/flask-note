### group\_by

根据某个字段进行分组，比如想要根据性别进行分组，来统计每个分组分别有多少人，那么可以使用以下代码来完成:

```
session.query(User.gender,func.ount(User.id)).group_by(User.gender).all()
```



