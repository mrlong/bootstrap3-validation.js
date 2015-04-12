庆国庆，今年2013国庆七天假没有出行。给国家，给社区，给bootstrap3贡献一份力量。 2013－10－2

bootstrap3-validation.js
author：mrlong  
home: http://www.mrlong.cn
========================

jQuery plugin for bootstrap3
由于在网上找到一个插件已不在维护了，并只支持bootstrap2 . 应项目要求自己写了一个。

![preview](https://github.com/mrlong/bootstrap3-validation.js/blob/master/test/test.png?raw=true)
![preview](https://github.com/mrlong/bootstrap3-validation.js/blob/master/test/test2.png?raw=true)
![preview](https://github.com/mrlong/bootstrap3-validation.js/blob/master/test/test3.png?raw=true)

##ChangeLog
 - 5. 1.0.4  修改在textarea没有type时的错误并扩展valid（）方法。 2014-6-15 巴西世界杯 英格兰1-意大利2
 - 4. 1.0.3  修改支持IE8，Array.indexOf() 改为 $.inArray()
 - 3. 1.0.2  增加基本表单与内联表单样式。
 - 2. 1.0.1  callback显示提示的信息。 2013-10-5
 - 1. 1.0.0  创建文件 
  

##功能参数
```
 check-type=
    required 不能为空，并在后面自动加*号
    url  表示 输入网址
    date 日期格式 xxxx-xx-xx
    mail 邮箱
    number 数字，可以整型，浮点型。
    char 
    chinese 中文
 mail-message="扩展提示内容" ， 可以扩展data-message,url-message  
 mixlength="6" 表示长度大于等于6
 range="2.1~3"   表示值在[2.1~3]之间，并check-type="number"
 range="2.1,2,4,5"   表示值在只能填现数字，并check-type="number" 


 例如:
  $("form").validation(function(obj,params){
     if (obj.id=='mail'){
       $.post("/verifymail",{mail :$(obj).val()},function(data){
         params.err = !data.success;
         params.msg = data.msg;
        });
     }},
     {reqmark:false}
    );
```

#使用方法：

## js:

```js
<script type="text/javascript">
 $(function(){
   //1. 简单写法：
   $("form").validation();
   $("button[type='submit']").on('click',function(event){
     // 2.最后要调用 valid()方法。
     if ($("form").valid(this,"error!")==false){
       //$("#error-text").text("error!"); 1.0.4版本已将提示直接内置掉，简化前端。
       return false;
     }
   })  })
</script>
```

###后台数据判断，如用户邮箱是否已注册过了。
```js
$("form").validation(function(obj,params){
     if (obj.id=='mail'){
       $.post("/verifymail",{mail :$(obj).val()},function(data){
         params.err = !data.success;
         params.msg = data.msg;
        });
     }},
     {reqmark:false}
    );
```

## html:
```html
  <form class="form-horizontal"  action="#" role="form">
      <div class="form-group">
        <label for="mail" class="col-sm-2 control-label">Email</label>
        <div class="col-sm-6">
          <input type="text" class="form-control" id="mail" placeholder="xxxx@qq.com" check-type="mail required">
        </div>
      </div>

      <div class="form-group">
        <label for="name" class="col-sm-2 control-label">用户名</label>
        <div class="col-sm-6">
          <input type="text" class="form-control" id="name" check-type="required" required-message="请填写你的大名。">
        </div>
      </div>

      <div class="form-group">
        <label for="pw1" class="col-sm-2 control-label">密码</label>
        <div class="col-sm-6">
          <input type="password" class="form-control" id="pw1" check-type="required" minlength="6">
        </div>
      </div>

      <div class="form-group">
        <label for="pw2" class="col-sm-2 control-label">确认密码</label>
        <div class="col-sm-6">
          <input type="password" class="form-control" id="pw2" check-type="required" minlength="6">
        </div>
      </div>  

      <div class="form-group">
        <label for="vercode" class="col-sm-2 control-label">验证码</label>
        <div class="col-sm-6">
          <input type="text" class="form-control" id="vercode" check-type="number" range="2.2,5">
        </div>
      </div>  

      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="submit" class="btn btn-primary col-sm-4">注册</button>
        </div>
      </div>

      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <span id="error-text" style="color: #FF0000;"></span>
        </div>
      </div>

    </form>
```

bootstrap3 validation
