## 上传文件

1.注意上传文件时，在form表单需要指定enctype="multipart/form-data"，不然上传文件不成功

```
    <form action="" method="post" enctype="multipart/form-data">
        <table>
            <tbody>
                <tr>
                    <td>头像:</td>
                    <td><input type="file" name="avatar"/></td>
                </tr>
                <tr>
                    <td>描述信息:</td>
                    <td><textarea name="desc"></textarea></td>
                </tr>
                <tr>
                    <td></td>
                    <td><input type="submit" value="提交"/></td>
                </tr>
            </tbody>
        </table>
    </form>
```

2.在后台获取上传文件，应该使用"request.files.get\("文件字段名"\)"

```
# 获取文件
avatar = request.files.get("avatar")

```



