js加密，前端和后端指定同一加密规则

```
$(function () {
    $('#sms-captcha-btn').click(function (event) {
        event.preventDefault();
        var self = $(this);
        var telephone = $("input[name='telephone']").val();
        if(!(/^1[345789]\d{9}$/.test(telephone))){
            zlalert.alertInfoToast("请输入正确的手机号码");
            return ;
        }
        var timestamp = (new Date).getTime();
        var sign = md5(timestamp+telephone+"A@^JIJw55a7832a@kddad@！&12=");
        zlajax.post({
            'url':'/c/sms_captcha/',
            'data':{
                'telephone':telephone,
                'timestamp':timestamp,
                'sign':sign,
            },
            'success':function (data) {
                // console.log(data)
                if (data['code'] == 200) {
                    zlalert.alertSuccessToast("短信验证码发送成功!");
                    self.attr('disabled', 'disabled');
                    //倒计时,每隔1秒执行1次
                    var timeCount = 6;
                    var timer = setInterval(function () {
                        timeCount--;
                        self.text(timeCount);
                        if (timeCount <= 0) {
                            self.removeAttr('disabled');
                            clearInterval(timer);
                            self.text("发送验证码");
                        }
                    }, 1000)
                }else{
                    zlalert.alertInfoToast(data["message"]);
                }
            }
        })
    })
})
```

```
from apps.forms import BaseForm
from wtforms import StringField
from wtforms.validators import regexp,InputRequired
import hashlib
class SMSCaptchaForm(BaseForm):
    salt = "A@^JIJw55a7832a@kddad@！&12="
    telephone = StringField(validators=[regexp(r'^1[345789]\d{9}')])
    timestamp = StringField(validators=[regexp(r'\d{13}')])
    sign = StringField(validators=[InputRequired()])

    def validate(self):
        result = super(SMSCaptchaForm,self).validate()
        if not result:
            return False
        telephone = self.telephone.data
        timestamp = self.timestamp.data
        sign = self.sign.data
        # md5(timestamp+telephone+salt)
        # md5函数必须要传入一个bytes类型的字符串进去
        # 从md5对象中获取字符串需要调用hexdigest()方法
        sign2 = hashlib.md5((timestamp+telephone+self.salt).encode('utf-8')).hexdigest()
        print("客户端提交的",sign)
        print("服务器提交的",sign2)
        if sign == sign2:
            return True
        else:
            False
```

视图以post方法重写

```
@bp.route('/sms_captcha/',methods=['POST'])
def sms_captcha():
    # telephone
    # timestamp
    # md5(ts+telephone+salt)
    form = SMSCaptchaForm(request.form)
    if form.validate():
        telephone = form.telephone.data
        captcha = Captcha.gene_text(4)
        if demo_sms_send.send_api(telephone,code=captcha):
            return restful.success()
        else:
            return restful.params_error(message="短信验证码发送失败！")
    else:
        return restful.params_error(message="参数错误")
```



