隐藏文本

```
<span style="display: none;" id="return-to-span">{{ return_to }}</span>
```

获取隐藏的文本

```
var return_to = $('#return-to-span').text();
```

判断return\_to参数值

```
    def get(self):
        return_to = request.referrer
        if return_to and return_to != request.url and safeutils.is_safe_url(return_to):
            return render_template('front/signup.html',return_to=return_to)
        else:
            return render_template('front/signup.html')
```



