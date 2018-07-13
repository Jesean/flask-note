## 对上传文件使用表单验证

1.定义表单的时候，对文件的字段，需要采用"FileField"这个类型

2.验证器应该从"flask\_wtf.file"中导入，使用“flask\_wtf.file.FileRequired”是用来验证文件上传是否为空，“flask\_wtf.file.FileAllowed”用来验证上传的文件的后缀名

3.在视图文件中，使用"from werkzeug.datastructures.CombinedMultiDict"，来把"request.form"与"request.files"来进行合并，再传给表单来做验证

```
form = UploadFrom(CombinedMultiDict([request.form,request.files]))
request.form.update(request.files)
```



