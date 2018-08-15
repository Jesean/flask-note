### 在网站中使用七牛存储文件

#### 安装sdk

```
pip install qiniu
```

#### 编写获取uptoken的接口

```
@app.route('/uptoken/')
def uptoken():
    # AK
    access_key = "xxxxxxx"
    # SK
    secret_key = "xxxxxxx"
    # 验证
    q = qiniu.Auth(access_key,secret_key)
    # 储存空间名字
    bucket = "tokimeki"
    token = q.upload_token(bucket)
    return jsonify({"uptoken":token})
```

![](/assets/173-01.png)

在前端中添加js的sdk:七牛为javascript提供了一个专门用来传文件的接口

```
<script src="https://cdn.staticfile.org/Plupload/2.1.1/moxie.js"></script>
<script src="https://cdn.staticfile.org/Plupload/2.1.1/plupload.dev.js"></script>
<script src="https://cdn.staticfile.org/qiniu-js-sdk/1.0.14-beta/qiniu.js"></script>
```

在前段添加zlqiniu.js，js文件封装了七牛的初始化和配置相关的参数

