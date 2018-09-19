# 通知模块接口

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

