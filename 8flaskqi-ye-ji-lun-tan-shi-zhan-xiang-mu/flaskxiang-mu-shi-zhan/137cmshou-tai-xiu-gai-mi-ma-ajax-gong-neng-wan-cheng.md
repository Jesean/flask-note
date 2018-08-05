在页面不刷新的情况下，异步加载把数据传给服务器

```
// $ ==> JQuery
$(function () {

    $("#submit").click(function (even) {
        //阻止表单按钮的提交表单的事件
        even.preventAndSave();

        var oldpwdElement = $("input[name=oldpwd]");
        var newpwdElement = $("input[name=newpwd]");
        var newpwd2Element = $("input[name=newpwd2]");

        var oldpwd = oldpwdElement.val();
        var newpwd = newpwdElement.val();
        var newpwd2 = newpwd2Element.val();

        //1.要在模板的meta中渲染一个crsf_token
        //2.在ajax请求的头部中设置X-CSRFtolen
        zlajax.post({
            'url':'/cms/resetpwd/',
            'data':{
                'oldpwd':oldpwd,
                'newpwd':newpwd,
                'newpwd2':newpwd2,
            },
            'success':function (data) {
                console.log(data);
            },
            'fail':function (error) {
                console.log(error);
            }
        })

    });
});
```



