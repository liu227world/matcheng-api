# 校园巡更接口

*	接口使用dwr方式

## 测试地址
```
js引用：
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/interface/XmsPatrolService.js"></script>
<script type="text/javascript" src="http://192.168.3.102:8081/mecwish/dwr/engine.js"></script>
跨域设置：
DWREngine.setMethod(DWREngine.ScriptTag);
XmsPatrolService._path = 'http://192.168.3.102:8081/mecwish/dwr';

```

## 目录

*   [添加或修改位置](#添加或修改位置)
*   [查询位置](#查询位置)
*   [根据位置编码查询位置](#根据位置编码查询位置)
*   [根据学校和位置名称查询位置列表](#根据学校和位置名称查询位置列表)
*   [根据线路查询位置列表](#根据线路查询位置列表)
*   [删除位置](#删除位置)
*   [添加或修改线路](#添加或修改线路)
*   [查询线路](#查询线路)
*   [根据学校和线路名称查询线路列表](#根据学校和线路名称查询线路列表)
*   [删除线路](#删除线路)
*   [添加或修改规则](#添加或修改规则)
*   [根据线路查询规则列表](#根据线路查询规则列表)
*   [查询我的指定日期的规则列表](#查询我的指定日期的规则列表)
*   [删除规则](#删除规则)
*   [添加巡更记录](#添加巡更记录)
*   [用户当前所有可巡位置](#用户当前所有可巡位置)
*   [用户一个规则下的可巡位置](#用户一个规则下的可巡位置)


## 添加或修改位置

```
var objectClass = 'SaveLocation';
var mcCode = '';
var param1 = 'aa3533f514c049bf868849718b9b9844';
var param2 = '位置';
var param3 = '位置或巡更说明';
var param4 = '标签1';
XmsPatrolService.saveObject(objectClass, mcCode, param1, param2, param3, param4, null, null, null, null, null, null, null, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 位置code，值为空时添加位置，不为空时修改位置
param1 | true | string | 组织code
param2 | true | string | 位置名称
param3 | true | string | 位置或巡更说明
param4 | true | string | 标签，用于位置的分类


## 查询位置

```
var objectClass = 'GetLocation';
var filter = 'mcCode=?'
var mcCode = '5e995a4b884743708891343dc562889c';
XmsPatrolService.getObject(objectClass, filter, mcCode, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 位置code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | code
field3 | string | 位置名称
field4 | string | 位置说明
field5 | string | 位置编码
field6 | string | 位置标签
field7 | string | 二维码地址
field8 | string | 创建时间
field9 | string | 修改时间
field10 | string | 组织code
field11 | string | 组织名称
field12 | string | 所在线路code的列表
field13 | string | 所在线路名称的列表


## 根据位置编码查询位置

```
var objectClass = 'GetLocation';
var filter = 'sn=?'
var param1 = '595259';
XmsPatrolService.getObject(objectClass, filter, null, param1, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 位置编码SN


#### 返回参数
见：[查询位置](#查询位置)


## 根据学校和位置名称查询位置列表

```
var objectClass = 'GetLocationList';
var filter = 'orgAndName=?'
var param1 = 'aa3533f514c049bf868849718b9b9844';
var param2 = '';
XmsPatrolService.getObjects(objectClass, null, filter, param1, param2, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 组织code
param2 | true | string | 位置名称


#### 返回参数
见：[查询位置](#查询位置)


## 根据线路查询位置列表

```
var objectClass = 'GetLocationList';
var filter = 'route=?'
var param1 = '';
XmsPatrolService.getObjects(objectClass, null, filter, param1, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 线路code


#### 返回参数
见：[查询位置](#查询位置)


## 删除位置
已加入线路的位置或已巡更位置不能删除

```
var objectClass = 'RemoveLocation';
var mcCode = '38a01e2351354d6fa3b5b2f9be54127b'
XmsPatrolService.removeObject(objectClass, mcCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 位置code


## 添加或修改线路

```
var objectClass = 'SaveRoute';
var mcCode = '7941b4a55c644f1b848a430301e4f8b7';
var param1 = 'aa3533f514c049bf868849718b9b9844';
var param2 = '卓信大厦消防检查';
var param3 = '所有消防栓检查、消防警报检查等';
var param4 = 'ea95d84c52db4da1a6bfb92dc127a1f7,fda8b2dfa6014c1faa95150bc1f15bc6';
var param5 = '5e995a4b884743708891343dc562889c,f45f572b166745feae8f02ab37676582';
    XmsPatrolService.saveObject(objectClass, mcCode, param1, param2, param3, param4, param5, null, null, null, null, null, null, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 位置code，值为空时添加，不为空时修改
param1 | true | string | 组织code
param2 | true | string | 线路名称
param3 | true | string | 线路说明
param4 | true | string | 扫码人code列表
param5 | true | string | 位置code列表


## 查询线路

```
var objectClass = 'GetRoute';
var filter = 'mcCode=?'
var mcCode = '7941b4a55c644f1b848a430301e4f8b7';
XmsPatrolService.getObject(objectClass, filter, mcCode, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 线路code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | code
field3 | string | 线路名称
field4 | string | 线路说明
field5 | string | 创建时间
field6 | string | 修改时间
field7 | string | 组织code
field8 | string | 组织名称
field9 | string | 扫码人code列表，多个以逗号隔开
field10 | string | 扫码人姓名列表，多个以逗号隔开
field11 | string | 位置code列表，多个以逗号隔开
field12 | string | 位置名称列表，多个以逗号隔开


## 根据学校和线路名称查询线路列表

```
var objectClass = 'GetRouteList';
var filter = 'orgAndName=?'
var param1 = 'aa3533f514c049bf868849718b9b9844';
var param2 = '';
XmsPatrolService.getObjects(objectClass, null, filter, param1, param2, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 组织code
param2 | true | string | 线路名称


#### 返回参数
见：[查询线路](#查询线路)


## 删除线路
已巡更的线路不能删除，删除时会同时删除线路规则、巡更人、巡更位置

```
var objectClass = 'RemoveRoute';
var mcCode = '7941b4a55c644f1b848a430301e4f8b7'
XmsPatrolService.removeObject(objectClass, mcCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 线路code


## 添加或修改规则

```
var objectClass = 'SaveRule';
var mcCode = '';
var param1 = '7941b4a55c644f1b848a430301e4f8b7';
var param2 = '2018-09-20 12:00:00';
var param3 = '2018-09-20 15:00:00';
var param4 = '86400000';
var param5 = '1';
var param6 = '2018-09-30 15:00:00';
XmsPatrolService.saveObject(objectClass, mcCode, param1, param2, param3, param4, param5, param6, null, null, null, null, null, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 规则code，值为空时添加，不为空时修改
param1 | true | string | 线路code
param2 | true | string | 开始时间，格式为 yyyy-MM-dd HH:mm:ss
param3 | true | string | 结束时间，格式为 yyyy-MM-dd HH:mm:ss
param4 | true | string | 循环周期，单位：ms
param5 | true | string | 巡更方式：1-一人扫；2-每个人必须扫
param6 | true | string | 关闭时间，格式为 yyyy-MM-dd HH:mm:ss


## 根据线路查询规则列表

```
var objectClass = 'GetRuleList';
var filter = 'route=?'
var param1 = '7941b4a55c644f1b848a430301e4f8b7';
XmsPatrolService.getObjects(objectClass, null, filter, param1, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 线路code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | code
field3 | string | 开始时间
field4 | string | 结束时间
field5 | string | 关闭时间
field6 | string | 周期
field7 | string | 巡更方式：1-一人扫；2-每个人必须扫
field8 | string | 线路code
field9 | string | 线路名称
field10 | string | 创建时间
field11 | string | 修改时间


## 查询我的指定日期的规则列表

```
var objectClass = 'GetRuleList';
var filter = 'userAndValid=?'
var param1 = 'ea95d84c52db4da1a6bfb92dc127a1f7';
var param2 = '2018-09-21';
XmsPatrolService.getObjects(objectClass, null, filter, param1, param2, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 用户code
param2 | true | string | 指定查询日期，格式为yyyy-MM-dd

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | code
field3 | string | 开始时间
field4 | string | 结束时间
field5 | string | 关闭时间
field6 | string | 周期
field7 | string | 巡更方式：1-一人扫；2-每个人必须扫
field8 | string | 线路code
field9 | string | 线路名称
field10 | string | 创建时间
field11 | string | 修改时间
field12 | string | 是否可以巡更：1-可巡；0-不可巡


## 删除规则
已巡更的规则不能删除

```
var objectClass = 'RemoveRule';
var mcCode = 'e091b5fa335d42e3beb302f37394db7a'
XmsPatrolService.removeObject(objectClass, mcCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
mcCode | true | string | 规则code


## 添加巡更记录

```
var objectClass = 'SavePatrolDetail';
var param2 = '595259';
var param3 = 'ea95d84c52db4da1a6bfb92dc127a1f7';
var param4 = '';
var param5 = '我是巡更内容啊啊啊';
var param6 = '1';
XmsPatrolService.saveObject(objectClass, null, null, param2, param3, param4, param5, param6, null, null, null, null, null, null, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param2 | true | string | 位置SN
param3 | true | string | 巡更人code
param4 | true | string | 巡更图片列表，多个以逗号隔开
param5 | true | string | 巡更说明
param6 | true | string | 巡更状态：0-异常；1-正常


## 用户当前所有可巡位置

```
var objectClass = 'GetLocationList';
var filter = 'validAll'
var param1 = '1d09c24a38f840c5c9f1a34e1a44ccfd';
XmsPatrolService.getObjects(objectClass, null, filter, param1, null, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 用户code

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | ID
field2 | string | code
field3 | string | 位置名称
field4 | string | 位置说明
field5 | string | 位置编码
field6 | string | 位置标签
field7 | string | 二维码地址
field8 | string | 创建时间
field9 | string | 修改时间
field10 | string | 组织code
field11 | string | 组织名称
field12 | string | 所在线路code的列表
field13 | string | 所在线路名称的列表
field14 | string | 是否已巡：1-已巡；0-未巡


## 用户一个规则下的可巡位置

```
var objectClass = 'GetLocationList';
var filter = 'validByRoute'
var param1 = '1d09c24a38f840c5c9f1a34e1a44ccfd';
var param2 = 'e091b5fa335d42e3beb302f37394db7a';
XmsPatrolService.getObjects(objectClass, null, filter, param1, param2, null,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
param1 | true | string | 用户code
param2 | true | string | 规则code

#### 返回参数

见：[用户当前所有可巡位置](#用户当前所有可巡位置)