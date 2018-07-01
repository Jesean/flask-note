### 类视图

之前的视图都是函数，所以一般简称为视图函数。其实视图也可以基于类来实现，类视图的好处是支持继承，但是类视图不能跟函数视图一样，写完类视图好需要通过 app.add\_urlrule\(urlrule,view\_func\)。以下将对两种类视图进行讲解:

### 标准视图:

标准视图继承自flask.views.View,并且在子类中必须实现 dispetch\_request方法，这个方法类似于视图函数，也要返回一个基于Response或者子类的对象，以下将用一个例子进行讲解:

```
class BaseView(views.View):
    # 自定义方法，用来获取模板路径
    def get_template_name(self):
        raise NotImplementedError()

    # 必须实现的方法，用来处理请求的
    def dispatch_request(self):
        if request.method != 'GET':
            return 'method error'

        # 这想从self.get_data()中获取函数，子类应该实现这个方法
        context = {'data':self.get_data()}
        return render_template(self.get_template_name(),**context)

class UserView(BaseView):
    # 实现从父类继承的获取模板路径的方法
    def get_template_name(self):
        return 'user.html'

    # 重写获取函数的方法
    def get_data(self):
        return [{
            'username':'false',
            'avatar':'http://www.baidu.com',
        }]

# 类视图通过add_url_rule方法和url做映射
app.add_url_rule('/users/',view_func=UserView.as_view('userview'))
```

### 基于调度方法的视图:

Flask提供了另外一种类视图flask.views.MethodView，对每个HTTP方法执行不同的函数\(映射到对应的方法的小写的同名方法上\)，还对 RESTful API尤其有用，例子:

```
class UserAPI(views.MethodView):
    #客户端通过get方法进行访问的时候执行的函数、
    def get(self):
    return jsonify({
        'username':'angle',
        'avator':'http://www.baidu.com',
    })

    # 当客户端通过post方法进行访问的时候执行的函数
    def post(self):
        return 'UNSUPPORTED'


# 通过add_url_rule添加类视图和url的映射，并且在as_view方法中指定该url的名称，方便url_for函数调用
app.add_url_rule('/myuser/',view_func=UserAPI.as_view('userapiview'))
```

用类视图的一个缺陷就是比较难用装饰器来装饰，比如有时候需要做权限验证的时候，比如:

```
def user_required(f)
    def decorator(*args,**kwargs):
        if not g.user:
            return 'auth failure'
        return f(*args,**kwargs)
    return decorator
```

如果要在类视图上进行装饰，只能在as\_view函数上进行装饰了，使用方式:

```
view = user_required(UserAPI.as_view('users'))
app.add_url_rule('/users/',views_func=view)
```

从flask 0.8 开始，还可以通过在类中添加decorators属性来实现对视图的装饰:

```
class UserAPI(views.MethodView):
    decorator = [user_required]
    ....
```

---

```
# 必须继承自views
class ListView(views.View):
    def dispatch_request(self):
        return "list view"

# 类.as_view(name) 返回一个函数,name:视图名
app.add_url_rule('/list/',endpoint='list',view_func=ListView.as_view('list'))
```

![](/assets/38.img1.png)

