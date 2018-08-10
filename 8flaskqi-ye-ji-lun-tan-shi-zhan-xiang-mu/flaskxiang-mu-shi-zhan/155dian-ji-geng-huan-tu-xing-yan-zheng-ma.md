修改验证码的细节

```
.captcha-addon{
    padding:0;
    /*溢出隐藏*/
    overflow: hidden;
}

.captcha-img{
    width:94px;
    height:32px;
    cursor:pointer;
}

<span class="input-group-addon captcha-addon">
    <img id="captcha-img" class="captcha-img" src="{{ url_for('front.graph_captcha') }}" alt="">
</span>
```



