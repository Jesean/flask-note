### 常用过滤器：

##### 'default'过滤器:
使用方式'{{value|default('默认值')}}',如果value这个'key'不存在，那么就会使用'default'过滤器提供的默认值。如果想使用类似于'python'中判断一个值是否为False，那么就必须要传递另外一个参数'{{value|default('默认值,boolean=True)}}'

可以使用'or' 来替代 'default('默认值',boolean=True)'
例如:'{{signature or 'angle'}}'.