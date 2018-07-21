### 输出字段:

对于一个视图函数，你可以指定好一些字段用于返回。以后可以使用ORM模型或者自定义的模型的时候，它会自动的获取模型中的相应的字段，生成json数据，然后再返回给客户端，这其中需要导入flask_restfu_.marshal\_with装饰器。并且需要写一个字典，来指示需要返回的字段，以及该字段的数据类型。

```
class ProfileView(Resource):
    resource_fileds = {
        'username':fields.String,
        'age':fields.Integer,
        'school':fields.String
    }
    
    @narshal_with(resource_fields)
    def get(self.user_id):
        user = User.query.get(user_id)
        return user
```

在get方法中，返回user的时候，flask\_restful会自动的读取user模型上的username以及age还有school属性。组装成一个json格式的字符串返回给客户端

