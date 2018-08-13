# 通知模块接口

*	接口使用dwr方式

## 测试地址
```
js引用：
<script type="text/javascript" src="http://www.wojiaxiaozhu.cn/mecwish/dwr/interface/NoticeService.js"></script>
<script type="text/javascript" src="http://www.wojiaxiaozhu.cn/mecwish/dwr/engine.js"></script>
跨域设置：
DWREngine.setMethod(DWREngine.ScriptTag);
NoticeService._path = 'http://www.wojiaxiaozhu.cn/mecwish/dwr';

```

## 目录

*   [发送或修改通知](#发送或修改通知)
*   [发送人的通知类型列表](#发送人的通知类型列表)
*   [接收人的通知类型列表](#接收人的通知类型列表)
*   [根据类型获取发通知列表](#根据类型获取发通知列表)
*   [根据类型获取收通知列表](#根据类型获取收通知列表)
*   [查询发送详情](#查询发送详情)
*   [查询接收详情](#查询接收详情)
*   [活动会议签到](#活动会议签到)
*   [根据发送的通知获取收通知列表](#根据发送的通知获取收通知列表)
*   [设置提醒时间](#设置提醒时间)


## 发送或修改通知

```

var mcCode = ''
var senderCode = '1'
var draft = 1;
var sendType = 1;
var sendTime = '2018-09-10 10:00:00'
var remind = 30;
var noticeType = 1;
var noticeTime = '2018-09-11 11:00:00'
var noticeAddress = '会议室'
var noticeContent = '教学安排aaaaaaaaaaaaaa'
var noticeNode = '终于'
var noticeImages = ''
var receiveUsers = '[{"code":"1","name":"张三"}]'

NoticeService.update(mcCode, senderCode, draft, sendType, sendTime,
    remind, noticeType, noticeTime, noticeAddress,
    noticeContent, noticeNode, noticeImages, receiveUsers, function(res){
        console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 发送通知code
senderCode | true | string | 发送人code 
draft | true | int | 是否保存为草稿(1-草稿；0-非草稿)：修改非草稿文档无效 
sendType | true | int | 发送类型（1-即时发送；2-定时发送） 
sendTime | true | string | 发送时间，定时发送有效 
remind | true | int | 提前几分钟提醒 
noticeType | true | int | 通知类型
noticeTime | true | string | 时间 
noticeAddress | true | string | 地点 
noticeContent | true | string | 内容 
noticeNode | true | string | 注意事项 
noticeImages | true | string | 图片列表 
receiveUsers | true | string | 接收人列表，格式为[{"code":"1","name":"张三"}]



## 发送人的通知类型列表

```

var senderCode = '1';

NoticeService.sendNoticeTypeList(senderCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
senderCode | true | string | 发送人code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
code | int | 类型唯一标志
msg | string | 类型名称
content | string | 类型下的第一条数据内容，html格式
contentCode | string | 类型下的第一条数据code


## 接收人的通知类型列表

```

var receiverCode = '1';

NoticeService.receiveNoticeTypeList(receiverCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
receiverCode | true | string | 接收人code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
code | int | 类型唯一标志
msg | string | 类型名称
content | string | 类型下的第一条数据内容，html格式
contentCode | string | 类型下的第一条数据code


## 根据类型获取发通知列表

```

var userCode = '1';
var typeCode = '1';
var page = 0;
var limit = 0;

NoticeService.noticeSendListByType(userCode, typeCode, page, limit,function(res){
	console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
userCode | true | string | 用户code
typeCode | true | string | 类型code
page | true | int | 第几页 （当前无效）
limit | true | int | 每页几条 （当前无效）


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | mcCode
field3 | string | status
field4 | string | 发送人code
field5 | string | 发送人姓名
field6 | string | 发送状态（2-草稿；1-已发送；0-待发送）
field7 | string | 发送类型（1-即时发送；2-定时发送）
field8 | string | 发送时间
field9 | string | 提醒时间
field10 | string | 二维码地址（该功能交由前端处理）
field11 | string | 通知类型
field12 | string | 时间
field13 | string | 地点
field14 | string | 内容
field15 | string | 提醒/科目
field16 | string | 图片列表
field17 | string | 接收人
field18 | string | 发送数量
field19 | string | 签到数量
field20 | string | 创建时间


## 根据类型获取收通知列表

```

var userCode = '1';
var typeCode = '1';
var page = 0;
var limit = 0;

NoticeService.noticeReceiveListByType('1','1','0','0',function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
userCode | true | string | 用户code
typeCode | true | string | 类型code
page | true | int | 第几页 （当前无效）
limit | true | int | 每页几条 （当前无效）


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | mcCode
field3 | string | status
field4 | string | 接收人code
field5 | string | 接收人姓名
field6 | string | 通知类型
field7 | string | 时间
field8 | string | 地点
field9 | string | 内容
field10 | string | 提醒/科目
field11 | string | 图片列表
field12 | string | 是否签到（1-是；0-否）
field13 | string | 签到时间
field14 | string | 创建时间/接收时间


## 查询发送详情

```

var sendCode = 'e0d4f84bf4ae4d46a07ba66730f1aa2a';

NoticeService.noticeSendByCode(sendCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sendCode | true | string | 发送code

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | mcCode
field3 | string | status
field4 | string | 发送人code
field5 | string | 发送人姓名
field6 | string | 发送状态（2-草稿；1-已发送；0-待发送）
field7 | string | 发送类型（1-即时发送；2-定时发送）
field8 | string | 发送时间
field9 | string | 提醒时间
field10 | string | 二维码地址（该功能交由前端处理）
field11 | string | 通知类型
field12 | string | 时间
field13 | string | 地点
field14 | string | 内容
field15 | string | 提醒/科目
field16 | string | 图片列表
field17 | string | 接收人
field18 | string | 发送数量
field19 | string | 签到数量
field20 | string | 创建时间


## 查询接收详情

```

var receiveCode = 'abd7575b3c734d7797f1aa23e0e62b0e';

NoticeService.noticeReceiveByCode(receiveCode,function(res){
    console.info( res );
});

```
#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
receiveCode | true | string | 接收code

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | mcCode
field3 | string | status
field4 | string | 接收人code
field5 | string | 接收人姓名
field6 | string | 通知类型
field7 | string | 时间
field8 | string | 地点
field9 | string | 内容
field10 | string | 提醒/科目
field11 | string | 图片列表
field12 | string | 是否签到（1-是；0-否）
field13 | string | 签到时间
field14 | string | 创建时间/接收时间



## 活动会议签到

```

var sendCode = 'e0d4f84bf4ae4d46a07ba66730f1aa2a';
var userCode = '1';
var signTime = '2018-09-11 10:30:12';

NoticeService.noticeSign(sendCode,userCode,signTime,function(res){
    console.info( res );
});

```
#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sendCode | true | string | 通知code
userCode | true | string | 用户code
signTime | true | string | 签到时间



## 根据发送的通知获取收通知列表

```

var sendCode = 'e0d4f84bf4ae4d46a07ba66730f1aa2a';
var page = 0;
var limit = 0;

NoticeService.noticeReceiveListBySend(sendCode,page,limit,function(res){
    console.info( res );
});

```
#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sendCode | true | string | 通知code
page | true | int | 第几页 （当前无效）
limit | true | int | 每页几条 （当前无效）

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | mcCode
field3 | string | status
field4 | string | 接收人code
field5 | string | 接收人姓名
field6 | string | 通知类型
field7 | string | 时间
field8 | string | 地点
field9 | string | 内容
field10 | string | 提醒/科目
field11 | string | 图片列表
field12 | string | 是否签到（1-是；0-否）
field13 | string | 签到时间
field14 | string | 创建时间/接收时间

## 设置提醒时间

```

var sendCode = 'e0d4f84bf4ae4d46a07ba66730f1aa2a';
var minute = 30;

NoticeService.noticeRemind(sendCode,minute,function(res){
    console.info( res );
});

```
#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sendCode | true | string | 通知code
minute | true | int | 提前几分钟提醒