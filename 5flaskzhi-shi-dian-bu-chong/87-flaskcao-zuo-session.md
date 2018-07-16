### flask操作session

* 设置session：设置session在session对象上进行设置的，通过"flask.session"对象上的一个"session.setdefault\(\)"方法或者字典来进行设置session信息

```
# one
session.setdefault("name","angle")
# two
session["name"] = "angle"
```

* 获取session:通过"session.get\(\)"方法获取



