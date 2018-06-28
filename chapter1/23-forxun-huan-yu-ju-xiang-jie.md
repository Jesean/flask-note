#### 'for ... in ...':'for'循环可以遍历任何一个序列包括列表、字典、元祖，并且可以进行反向遍历

##### 普通的遍历

```
<ul>
{% for user in users %}
<li>{{user.username|e}}</li>
{% endfor %}
</ul>
```

##### 遍历字典:

```
<dl>
	{% for key,value in my_dict_iteritems() %}
	<dt>{{key|e}}</dt>
	<dd>{{value|e}}</dd>
	{% endfor %}
</dl>
```

#### 并且'Jinja2'中的'for'循环还包含以下遍历，可以用来获取当前的遍历状态:



loop.index:当前迭代的索引\(从i开始\)

loop.index0:当前迭代的索引\(从0开始\)

loop.first:是否是第一次迭代，返回True或者False

loop.last:是否是最后一次迭代，返回True或者False

loop.length:序列的长度



另外，不可以使用'continue'和'break'表达式来控制循环的执行

