# 微信相关接口

*	接口使用dwr方式

## 测试地址
```
js引用：
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/interface/CartService.js"></script>
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/engine.js"></script>
跨域设置：
DWREngine.setMethod(DWREngine.ScriptTag);
CartService._path = 'http://192.168.3.102:8081/mecwish/dwr';

```

## 目录

*   [根据卡号查询卡信息](#根据卡号查询卡信息)


## 根据卡号查询卡信息

```
var objectClass = 'FixedCommodity';
var cardId = '1555670538';
CartService.getObejct(objectClass, cardId, null, null, null, function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
cardId | true | string | 十进制或十六进制卡号


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | id
field2 | string | code
field3 | string | 名称
field4 | string | 介绍
field5 | string | 卡号（十进制）
field6 | string | 卡类型
field7 | string | 
field8 | string | 通话时间，单位：分钟
field9 | string | 
field10 | string | 面值，单位：元
field11 | string | 
field12 | string | 过期时间
field13 | string | 过期类型
field14 | string | 
field15 | string | 出售金额，单位：元
field16 | string | 出售状态：0-销售中；1-已售出；2-已作废
field17 | string | 售出时间
field18 | string | 权重
field19 | string | 最后修改时间
field20 | string | 
field21 | string | 卡号（十六进制）
field22 | string | 出售状态说明
field23 | string | 亲情号码code
field24 | string | 号码1
field25 | string | 号码2
field26 | string | 号码3