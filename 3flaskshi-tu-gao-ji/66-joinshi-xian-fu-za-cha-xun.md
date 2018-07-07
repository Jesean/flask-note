### join方法

join查询分为两种，一种是inner join,另一种是outer join。默认的是inner join,如果指定left join或者是right join则为outer join。如果想要查询User及其对应的Address，则可以通过以下方式来实现:

```
for u,a in session.query(User,Address).filter(User.id == Address.user_id).all()
    print u
    print a
```



