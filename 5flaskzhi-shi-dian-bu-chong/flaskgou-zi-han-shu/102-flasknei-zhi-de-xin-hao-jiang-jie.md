### flask内置9种信号

* flask.template\_rendered:模板渲染完毕后发送

```
def template_rendered_func(sender,template,context):
        print("sender:{}".format(sender))
        print("template:{}".format(template))
        print("context:{}".format(context))
template_rendered.connect(template_rendered_func)
```

* flask.request\_started:请求开始之前，在到达视图函数之前发送，订阅者可以调用request之类的标准全局代理访问请求
* flask.request\_finished:请求结束时，在响应发送给客户端之前发送，可以传递response
* flask.request_tearing_down



