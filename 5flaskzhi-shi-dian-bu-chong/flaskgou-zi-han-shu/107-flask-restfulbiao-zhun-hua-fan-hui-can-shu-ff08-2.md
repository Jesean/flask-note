### 重命名属性

重命名属性字段

```
# 更改content属性的命名
resource_fields = {
        'title':fields.String,
        '内容':fields.String(attribute='content'),
    }
```



