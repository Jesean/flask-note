banner.js

```
$(function () {
   zlqiniu.setUp({
       'domain':'http://pdhjzz2pa.bkt.clouddn.com/',
       'browse_btn':'upload-btn',
       'uptoken_url':'/c/uptoken/',
       'success':function (up,file,info) {
           var imageInput = $("input[name='image_url']");
           imageInput.val(file.name)
       }
   });
});
```



