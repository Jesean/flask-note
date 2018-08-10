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
if (return_to){
    window.location = return_to;
}else{
    //跳转到首页
    window.location = '/';
}
```



