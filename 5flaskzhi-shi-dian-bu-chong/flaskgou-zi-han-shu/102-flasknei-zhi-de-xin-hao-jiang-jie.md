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
* flask.got\_request.exception:在请求过程中抛出异常时发送，异常本身会通过exception传递到订阅的函数
* flask.request\_tearing\_down:请求被销毁的时候发送，即使在请求过程中发生异常，也会发送
* flask.appcontext\_tearing\_down:在应用上下文销毁的时候发送，它总是会被调用



