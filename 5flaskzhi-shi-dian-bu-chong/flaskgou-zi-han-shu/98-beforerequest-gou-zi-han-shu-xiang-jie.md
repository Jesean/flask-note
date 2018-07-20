befor\_first\_request:处理第一次请求之前执行

```
@app.before_first_request
def first_request():
    print("before_first_request")
```

before\_request:在每次请求之前执行。通常可以用这个装饰器来给视图函数增加一些变量

