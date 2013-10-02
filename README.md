bootstrap3-validation.js
========================

jQuery plugin for bootstrap3

由于在网上找到一个插件已不在维护了，并只支持bootstrap2 . 应项目要求自己写了一个。

 *
 * check-type=
 *    required 不能为空，并在后面自动加*号
 *    url  表示 输入网址
 *    date 日期格式 xxxx-xx-xx
 *    mail 邮箱
 *    char
 *    chinese 
 * mixlength="6" 表示长度大于等于6
 * range="2.1~3"   表示值在[2.1~3]之间，并check-type="number"
 * range="2.1,2,4,5"   表示值在只能填现数字，并check-type="number" 
 *
 *
 * 例如:
 * $("form").validation(function(obj,params){
 *     if (obj.id=='mail'){
 *       $.post("/verifymail",{mail :$(obj).val()},function(data){
 *         params.err = !data.success;
 *         params.msg = data.msg;
 *       });
 *     }},
 *     {reqmark:false}
 *   );


bootstrap3 validation
