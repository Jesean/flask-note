### 重命名属性

重命名属性字段

```
# 更改content属性的命名
resource_fields = {
        'title':fields.String,
        '内容':fields.String(attribute='content'),
    }
------------------------------------------------------
{
    "title": "angle",
    "内容": "angle"
}
```

### 默认值

为指定字段设置默认值

```
resource_fields = {
        'content':fields.String(default="angle"),
    }
```

### 复杂结构

使用fields.List可以使字段的值为列表，使用fields.Nested可以使字段的值为字典

```
class ProfileView(Resource):
    resource_field = {
        'username':fields,String,
        'age':fields.Integer,
        'school':fields.String,
        'tags':fields.List(fields.String),
        'more':fields.Nested{{
            'signature':fields.String,
        }}
    }
```

---

flask_restful_demo.py

