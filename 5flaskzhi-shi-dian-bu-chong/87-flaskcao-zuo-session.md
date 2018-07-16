### flask操作session

* 设置session：设置session在session对象上进行设置的，通过"flask.session"对象上的一个"session.setdefault\(\)"方法或者字典来进行设置session信息

```
# one
session.setdefault("name","angle")
# two
session["name"] = "angle"
```

* 获取session:通过"session.get\(\)"方法获取

```
name = session.get("name")
```

* 删除指定session:通过“session.pop\(\)”方法删除指定的session值

```
# 删除指定session
session.pop("name")
```

* 清除所有的session值

```
# 清除所有session
session.clear()
```



