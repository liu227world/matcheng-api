# 微信相关接口

*	接口使用dwr方式

## 测试地址
```
js引用：
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/interface/NewWeixinService.js"></script>
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/engine.js"></script>
跨域设置：
DWREngine.setMethod(DWREngine.ScriptTag);
NewWeixinService._path = 'http://192.168.3.102:8081/mecwish/dwr';

```

## 目录

*   [通过短信验证码实现微信绑定](#通过短信验证码实现微信绑定)


## 通过短信验证码实现微信绑定

```
var wishCode = '1';
var openId = 'oRjaiju6hhexBjz7v_dKbP_BHrw8';
var phone = '18967103225';
var code = '0000';//测试验证码“0000”
var url = 'https://www.baidu.com';
NewWeixinService.binding(wishCode, openId, phone, code, url, function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
wishCode | true | string | wishAccountCode
openId | true | string | 用户在公众号下的openId
phone | true | string | 手机号
code | true | string | 验证码
url | true | string | 跳转链接


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
responseCode | int | code,值为0时成功，否则失败
responseText | string | 返回信息说明
responseParam1 | string | 跳转链接