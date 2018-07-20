### flask内置9种信号

* template\_rendered:模板渲染完毕后的信号

```
def template_rendered_func(sender,template,context):
        print("sender:{}".format(sender))
        print("template:{}".format(template))
        print("context:{}".format(context))
template_rendered.connect(template_rendered_func)
```

* request\_started:模板开始渲染
* request\_finished:模板完成渲染
* got\_request.exception:在请求过程中抛出异常时发送，异常本身会通过exception传递到订阅的函数
* request\_tearing\_down:request对象被销毁的信号
* got\_request\_exception:视图函数发生异常的信号
* appcontext\_tearing\_down:在应用上下文销毁的时候发送，它总是会被调用
* appcontext\_pushed
* appcontext\_poped
* message\_flashed



