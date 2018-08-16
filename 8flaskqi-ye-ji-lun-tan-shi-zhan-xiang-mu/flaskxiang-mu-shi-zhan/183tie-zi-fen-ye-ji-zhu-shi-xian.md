### 1.相关链接

flask Paginate:https://flask-paginate.readthedocs.io/en/latest/

### 2.添加测试数据

```
# 添加测试帖子数据
@manager.command
def create_test_post():
    for i in range(1,205):
        title = "标题{}".format(i)
        content = "内容:{}".format(i)
        board = BoardModel.query.first()
        author = FrontUser.query.first()
        post = PostModel(title=title,content=content)
        post.board = board
        post.author = author
        db.session.add(post)
        db.session.commit()
    print("添加帖子测试完成")
```

### 3.安装

```

```



