
# 电子班牌后台接口

## 目录

*   [查询教师列表](#查询教师列表)
*   [查询教师列表分页对象](#查询教师列表分页对象)
*   [添加菜单](#添加菜单)
*   [修改菜单](#修改菜单)
*   [删除菜单](#删除菜单)
*   [查询一条菜单](#查询一条菜单)
*   [查询菜单列表](#查询菜单列表)
*   [查询角色列表](#查询角色列表)
*   [查询租户列表](#查询租户列表)
*   [查询角色或用户的菜单树](#查询角色或用户的菜单树)
*   [查询全部菜单树](#查询全部菜单树)
*   [设置角色的菜单权限](#设置角色的菜单权限)

*   [添加设备](#添加设备)
*   [修改设备](#修改设备)
*   [删除设备](#删除设备)
*   [查询一台设备](#查询一台设备)
*   [查询设备列表](#查询设备列表)

*   [查询模式列表](#查询模式列表)
*   [查询区块列表](#查询区块列表)
*   [查询学校列表](#查询学校列表)
*   [查询学校列表分页对象](#查询学校列表分页对象)
*   [查询班级列表](#查询班级列表)
*   [查询班级列表分页对象](#查询班级列表分页对象)

*   [添加模式设置](#添加模式设置)
*   [修改模式设置](#修改模式设置)
*   [删除模式设置](#删除模式设置)
*   [查询一条模式设置](#查询一条模式设置)
*   [查询模式设置列表](#查询模式设置列表)
*   [查询模式设置列表分页对象](#查询模式设置列表分页对象)

*   [添加参数设置](#添加参数设置)
*   [修改参数设置](#修改参数设置)
*   [删除参数设置](#删除参数设置)
*   [查询一条参数设置](#查询一条参数设置)
*   [查询参数设置列表](#查询参数设置列表)
*   [查询参数设置列表分页对象](#查询参数设置列表分页对象)

*   [添加文章](#添加文章)
*   [修改文章](#修改文章)
*   [删除文章](#删除文章)
*   [查询一条文章](#查询一条文章)
*   [查询文章列表](#查询文章列表)
*   [查询文章列表分页对象](#查询文章列表分页对象)

*   [添加图片](#添加图片)
*   [修改图片](#修改图片)
*   [删除图片](#删除图片)
*   [查询一张图片](#查询一张图片)
*   [查询图片列表](#查询图片列表)
*   [查询图片列表分页对象](#查询图片列表分页对象)

*   [添加视频](#添加视频)
*   [修改视频](#修改视频)
*   [删除视频](#删除视频)
*   [查询一个视频](#查询一个视频)
*   [查询视频列表](#查询视频列表)
*   [查询视频列表分页对象](#查询视频列表分页对象)

*   [查询消息列表](#查询消息列表)
*   [查询消息列表分页对象](#查询消息列表分页对象)

*   [查询展示内容列表](#查询展示内容列表)
*   [查询展示内容列表分页对象](#查询展示内容列表分页对象)

*   [查询一条班牌运行状态信息](#查询一条班牌运行状态信息)
*   [查询班牌运行状态列表](#查询班牌运行状态列表)
*   [查询班牌运行状态列表分页对象](#查询班牌运行状态列表分页对象)

*   [添加课程](#添加课程)
*   [修改课程](#修改课程)
*   [删除课程](#删除课程)
*   [查询一个课程](#查询一个课程)
*   [查询课程列表](#查询课程列表)
*   [查询课程列表分页对象](#查询课程列表分页对象)

*   [调整班级学生](#调整班级学生)

*   [添加课表](#添加课表)
*   [修改课表](#修改课表)
*   [删除课表](#删除课表)
*   [查询一条课表](#查询一条课表)
*   [查询课表列表](#查询课表列表)
*   [查询课表列表分页对象](#查询课表列表分页对象)

*   [查询走班考勤列表](#查询走班考勤列表)
*   [查询走班考勤列表分页对象](#查询走班考勤列表分页对象)

*   [添加通知](#添加通知)
*   [修改通知](#修改通知)
*   [删除通知](#删除通知)
*   [查询一条通知](#查询一条通知)
*   [查询通知列表](#查询通知列表)
*   [查询通知列表分页对象](#查询通知列表分页对象)


## 查询教师列表

```
请求地址：/teacher/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
name | false | string | 教师姓名 
phone | false | string | 教师手机号 
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "cuid": "17090314030115258",
        "tname": "13093725817",
        "ofuserName": "13093725817",
        "orgNames": "媒成科技有限公司,2班,1班,正常班级,初一（1）班,教务处,学生处,后勤处,测试部门,教职工组01,教职工组02",
        "positionCode": "1001",
        "positionName": "校长",
        "tenantId": "18790591074",
        "phone": "13093725817",
        "picSrc": "upload/picSrc/teacher/18790591074/17090314030115258.jpg",
        "createTime": "2017-09-14 15:01:15"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
cuid | string | 教师ID
tname  | string | 教师姓名
ofuserName | string | 登录用户名 
orgNames | string | 所在的组织（学校、班级等）
positionCode | string | 职务code
positionName | string | 职务名称
tenantId | string | 租户ID
phone | string | 手机号
picSrc | string | 头像路径
createTime | string | 创建时间


## 查询教师列表分页对象

```
请求地址：/teacher/pager

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
name | false | string | 教师姓名 
phone | false | string | 教师手机号 

#### 返回结果

*** JSON示例 ***

```

{
    "page": 1,
    "limit": 1,
    "total": 939,
    "pageSize": 939,
    "first": true,
    "last": false
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
page | int | 页码
limit  | int | 每页数量
total | int | 总数量 
pageSize | int | 总页数
first | boolean | 是否首页
last | boolean | 是否尾页


## 添加菜单

```
请求地址：/sidebar/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | true | string | 菜单名称 
url | false | string | 访问路径 
icon | false | string | 菜单icon，Font Awesome图标库html片段，如“<i class="fa fa-dashboard"></i>” 
sort | false | int | 从小到大排序 
parentId | false | int | 上级菜单ID
index1 | false | string | 对应一级菜单活动标志
index2 | false | string | 对应二级菜单活动标志

#### 返回结果

*** 返回值为空 ***


## 修改菜单

```
请求地址：/sidebar/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 菜单ID
title | true | string | 菜单名称 
url | false | string | 访问路径 
icon | false | string | 菜单icon，Font Awesome图标库html片段，如“<i class="fa fa-dashboard"></i>” 
sort | false | int | 从小到大排序 
parentId | false | int | 上级菜单ID
index1 | false | string | 对应一级菜单活动标志
index2 | false | string | 对应二级菜单活动标志

#### 返回结果

*** 返回值为空 ***


## 删除菜单

```
请求地址：/sidebar/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 菜单ID

#### 返回结果

*** 返回值为空 ***


## 查询一条菜单

```
请求地址：/sidebar/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 菜单ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 2,
    "title": "学生列表",
    "url": "/user-student",
    "icon": "<i class=\"fa fa-circle-o\"></i>",
    "sort": 1,
    "parentId": 1,
    "parentTitle": "用户管理",
    "index1": "user",
    "index2": "student",
    "createTime": "2018-05-17 10:42:54",
    "updateTime": "2018-05-17 10:42:54",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | 菜单ID
title  | string | 菜单名称
url | string | 访问路径 
icon | string | 菜单icon，FontAwesome图标库html片段，如“<i class="fa fa-dashboard"></i>”
sort | int | 从小到大排序
parentId | int | 上级菜单ID
parentTitle | string | 上级菜单名称
index1 | string | 对应一级菜单活动标志
index2 | string | 对应二级菜单活动标志
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询菜单列表

```
请求地址：/sidebar/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | false | string | 菜单名称，用于模糊查询
url | false | string | 访问路径，用于模糊查询
parentId | false | int | 上级菜单ID
page | false | int | 页码
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "用户管理",
        "url": "",
        "icon": "<i class=\"fa fa-dashboard\"></i>",
        "sort": 1,
        "parentId": "",
        "parentTitle": "",
        "index1": "user",
        "index2": "",
        "createTime": "2018-05-17 10:42:54",
        "updateTime": "2018-05-17 10:42:54",
        "deleted": 0
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | 菜单ID
title  | string | 菜单名称
url | string | 访问路径 
icon | string | 菜单icon，FontAwesome图标库html片段，如“<i class="fa fa-dashboard"></i>”
sort | int | 从小到大排序
parentId | int | 上级菜单ID
parentTitle | string | 上级菜单名称
index1 | string | 对应一级菜单活动标志
index2 | string | 对应二级菜单活动标志
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询角色列表

```
请求地址：/role/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
roleName | false | string | 角色名称 
tenantId | false | long | 租户ID 
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "roleId": 310100,
        "roleName": "系统管理员",
        "isvalid": 1,
        "parentRoleId": 0,
        "parentRoleName": "",
        "tenantId": 310100,
        "tenantName": "上海招商",
        "positionCode": "",
        "positionName": ""
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
roleId | string | 角色ID
roleName  | string | 角色名称
isvalid | string | 是否有效：1-有效；0-无效 
parentRoleId | string | 上级角色ID
parentRoleName | string | 上级角色名称
tenantId | string | 租户ID
tenantName | string | 租户名称
positionCode | string | 职务code
positionName | string | 职务名称


## 查询租户列表

```
请求地址：/tenant/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
name | false | string | 租户名称

#### 返回结果

*** JSON示例 ***

```

[
    {
        "tenantId": "18790591074",
        "tenantName": "媒成科技",
        "createTime": "2016-07-26 10:47:13",
        "invalidTime": "2019-10-26 00:00:00",
        "status": 1,
        "companyName": "媒成科技",
        "imageName": "/upload/logo/logo20130131090834.png"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
tenantId | string | 租户ID
tenantName  | string | 租户名称
createTime | string | 创建时间 
invalidTime | string | 到期时间
status | string | 状态？
companyName | string | 公司名称
imageName | string | 头像地址


## 查询角色或用户的菜单树

```
请求地址：/sidebar/role/tree

请求类型：GET

请求说明：先根据角色ID查询；如果为空，根据用户名查询；只有一个参数生效，且至少需要一个参数
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
roleId | false | long | 角色ID
username | false | string | 用户名

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "用户管理",
        "url": "",
        "icon": "<i class=\"fa fa-dashboard\"></i>",
        "sort": 4,
        "parentId": "",
        "parentTitle": "",
        "index1": "user",
        "index2": "",
        "createTime": "2018-05-17 13:06:51",
        "updateTime": "2018-05-17 15:45:50",
        "deleted": 0,
        "children": [
            {
                "id": 2,
                "title": "学生列表",
                "url": "/user-student",
                "icon": "<i class=\"fa fa-circle-o\"></i>",
                "sort": 1,
                "parentId": 1,
                "parentTitle": "用户管理",
                "index1": "user",
                "index2": "student",
                "createTime": "2018-05-17 13:06:51",
                "updateTime": "2018-05-17 13:06:51",
                "deleted": 0
            }
        ]
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | 菜单ID
title  | string | 菜单名称
url | string | 访问路径 
icon | string | 菜单icon，FontAwesome图标库html片段，如“<i class="fa fa-dashboard"></i>”
sort | int | 从小到大排序
parentId | int | 上级菜单ID
parentTitle | string | 上级菜单名称
index1 | string | 对应一级菜单活动标志
index2 | string | 对应二级菜单活动标志
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是
children | list | 下级菜单列表

## 查询全部菜单树

```
请求地址：/sidebar/all/tree

请求类型：GET

```

#### 请求参数

*** 无参数 ***

#### 返回结果

*** 示例和字段说明参考“查询角色或用户的菜单树”接口 ***


## 设置角色的菜单权限

```
请求地址：/sidebar/auth/

请求类型：GET

请求说明：参数 sidebarIds 是全部的权限，包含一级菜单和二级菜单
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
roleId | false | long | 角色ID
sidebarIds | false | string | 一个或多个菜单ID拼装的字符串，以逗号（,）隔开

#### 返回结果

*** 返回值为空 ***


## 添加设备

```
请求地址：/device/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | true | string | 设备名称 
model | true | string | 设备品牌、型号 
intro | false | string | 设备说明
category | false | int | 设备类型：1-班级班牌 
sn | false | string | 设备编号
tenantId | false | string | 租户ID
schoolId | false | string | 学校ID
classId | false | string | 班级ID
installTime | false | string | 安装时间
installPlace | false | string | 安装位置

#### 返回结果

*** 返回值为空 ***


## 修改设备

```
请求地址：/device/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | true | string | 设备名称 
model | true | string | 设备品牌、型号 
intro | false | string | 设备说明
category | false | int | 设备类型：1-班级班牌 
sn | false | string | 设备编号
tenantId | false | string | 租户ID
schoolId | false | string | 学校ID
classId | false | string | 班级ID
installTime | false | string | 安装时间
installPlace | false | string | 安装位置

#### 返回结果

*** 返回值为空 ***


## 删除设备

```
请求地址：/device/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 设备ID

#### 返回结果

*** 返回值为空 ***


## 查询一台设备

```
请求地址：/device/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 设备ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "title": "电子班牌哈哈哈",
    "model": "华为P10",
    "intro": "这是一个手机",
    "category": "1",
    "tenantId": "",
    "schoolId": "",
    "classId": "",
    "installTime": "2018-05-18 10:19:44",
    "installPlace": "3幢6楼入口",
    "runStatus": "",
    "androidVersion": "",
    "softVersion": "",
    "dpi": "",
    "startTime": "",
    "styleId": "",
    "styleTitle": "",
    "createTime": "2018-05-18 10:17:57",
    "updateTime": "2018-05-18 10:19:45",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
title  | string | 设备名称
model | string | 设备品牌、型号 
intro | string | 设备说明
category | int | 设备类型：1-班级班牌
tenantId | string | 租户ID
schoolId | string | 学校ID
classId | string | 班级ID
installTime | string | 安装时间
installPlace | string | 安装位置
runStatus | int | 运行状态：1-正常；0-异常
androidVersion | string | 安卓版本
softVersion | string | 班牌软件版本
dpi | string | 分辨率
startTime | string | 上次启动时间
styleId | int | 当前运行模式ID
styleTitle | string | 当前运行模式名称
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询设备列表

```
请求地址：/device/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | false | string | 设备名称
model | false | string | 设备品牌、型号
schoolId | false | string | 学校ID
classId | false | string | 班级ID
page | false | int | 页码
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "电子班牌哈哈哈",
        "model": "华为P10",
        "intro": "这是一个手机",
        "category": "1",
        "tenantId": "",
        "schoolId": "",
        "classId": "",
        "installTime": "2018-05-18 10:19:44",
        "installPlace": "3幢6楼入口",
        "runStatus": "",
        "androidVersion": "",
        "softVersion": "",
        "dpi": "",
        "startTime": "",
        "styleId": "",
        "styleTitle": "",
        "createTime": "2018-05-18 10:17:57",
        "updateTime": "2018-05-18 10:19:45",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一台设备”接口 ***


## 查询模式列表

```
请求地址：/style/all

请求类型：GET

请求说明：查询所有的模式列表，不分页
```

#### 请求参数

*** 无参数 ***

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "公告模式",
        "intro": "学校公告信息",
        "sort": 1,
        "createTime": "2018-05-18 11:47:03",
        "updateTime": "2018-05-18 11:47:03",
        "deleted": 0
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
title  | string | 模式名称
intro | string | 模式说明
sort | int | 从小到大排序
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询区块列表

```
请求地址：/block/all

请求类型：GET

请求说明：查询所有的区块列表，不分页
```

#### 请求参数

*** 无参数 ***

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "班级窗口1",
        "intro": "班级窗口1",
        "styleId": 2,
        "styleTitle": "宣传模式",
        "sort": 1,
        "createTime": "2018-05-21 14:13:08",
        "updateTime": "2018-05-21 14:13:08",
        "deleted": 0
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
title  | string | 区块名称
intro | string | 区块说明
styleId | int | 所属模式ID
styleTitle | string | 所属模式标题
sort | int | 从小到大排序
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是

## 查询学校列表

```
请求地址：/organization/schools

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
name | false | string | 学校名称
tenantId | false | string | 租户ID
page | false | int | 页码
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "schoolID": "10061006",
        "schoolName": "爱婴博士幼儿园",
        "tenantId": "15306811177",
        "createTime": "2017-07-28 16:33:32"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
schoolID | string | 学校ID
schoolName  | string | 学校名称
tenantId | string | 租户ID
createTime | string | 添加时间


## 查询学校列表分页对象

*** 略 ***


## 查询班级列表

```
请求地址：/organization/classes

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
page | false | int | 页码
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "classID": "1104100110021005",
        "className": "大(1)班",
        "tenantId": "160609120219",
        "createTime": "2016-06-09 12:06:35"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
classID | string | 班级ID
className  | string | 班级名称
tenantId | string | 租户ID
createTime | string | 添加时间


## 查询班级列表分页对象

*** 略 ***


## 添加模式设置

```
请求地址：/style-change/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classId | true | string | 班级ID
styleId | true | int | 模式ID
changeTime | true | string | 切换时间，格式位：1990-01-01 10:30:00，有效值为时间，日期为补全字符串，无实际作用

#### 返回结果

*** 返回值为空 ***


## 修改模式设置

```
请求地址：/style-change/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
schoolId | true | string | 学校ID 
classId | true | string | 班级ID
styleId | true | int | 模式ID
changeTime | true | string | 切换时间，格式位：1990-01-01 10:30:00，有效值为时间，日期为补全字符串，无实际作用

#### 返回结果

*** 返回值为空 ***


## 删除模式设置

```
请求地址：/style-change/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一条模式设置

```
请求地址：/style-change/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10011001",
    "schoolName": "中国儿童中心实验幼儿园",
    "classId": "1001100110011001",
    "className": "大（1）班",
    "styleId": 1,
    "styleName": "公告模式",
    "changeTime": "1970-01-01 16:30:00",
    "createTime": "2018-05-20 15:15:03",
    "updateTime": "2018-05-20 15:24:14",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classId | string | 班级ID
className | int | 班级名称
styleId | int | 切换模式ID
styleName | string | 模式名称
changeTime | string | 切换模式时间，有效值为时间，日期无效
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询模式设置列表

```
请求地址：/style-change/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
classId | false | string | 班级ID
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10011001",
        "schoolName": "中国儿童中心实验幼儿园",
        "classId": "1001100110011001",
        "className": "大（1）班",
        "styleId": 1,
        "styleName": "公告模式",
        "changeTime": "1970-01-01 16:30:00",
        "createTime": "2018-05-20 15:15:03",
        "updateTime": "2018-05-20 15:24:14",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条模式设置”接口 ***

## 查询模式设置列表分页对象

*** 略 ***



## 添加参数设置

```
请求地址：/setup/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classId | true | string | 班级ID
fontSize | false | int | 文字大小
fontColor | false | string | 文字颜色
playType | false | int | 播放方式：1-左右滚动；2-上下滚动；3-静止；4-不显示；默认1
playSpeed | false | int | 播放速度，play_type为1或2时生效：1-慢速；2-中速；3-快速；默认2
playShow | false | int | 查看显示时间：10秒、30秒、60秒、只允许刷卡关闭（999999秒）；默认30秒
openTime | false | string | 开机时间，格式为“1990-10-10 10:30:00”，有效值为时间，日期为补偿字符串
closeTime | false | string | 关机时间，格式为“1990-10-10 10:30:00”，有效值为时间，日期为补偿字符串
brightness | false | int | 屏幕亮度（百分比，0到100的整数）
contrast | false | int | 对比度（百分比，0到100的整数）
volume | false | int | 音量（百分比，0到100的整数）

#### 返回结果

*** 返回值为空 ***


## 修改参数设置

```
请求地址：/setup/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
schoolId | true | string | 学校ID 
classId | true | string | 班级ID
fontSize | false | int | 文字大小
fontColor | false | string | 文字颜色
playType | false | int | 播放方式：1-左右滚动；2-上下滚动；3-静止；4-不显示；默认1
playSpeed | false | int | 播放速度，play_type为1或2时生效：1-慢速；2-中速；3-快速；默认2
playShow | false | int | 查看显示时间：10秒、30秒、60秒、只允许刷卡关闭（999999秒）；默认30秒
openTime | false | string | 开机时间，格式为“1990-10-10 10:30:00”，有效值为时间，日期为补偿字符串
closeTime | false | string | 关机时间，格式为“1990-10-10 10:30:00”，有效值为时间，日期为补偿字符串
brightness | false | int | 屏幕亮度（百分比，0到100的整数）
contrast | false | int | 对比度（百分比，0到100的整数）
volume | false | int | 音量（百分比，0到100的整数）

#### 返回结果

*** 返回值为空 ***


## 删除参数设置

```
请求地址：/setup/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一条参数设置

```
请求地址：/setup/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10011001",
    "schoolName": "中国儿童中心实验幼儿园",
    "classId": "1001100110011001",
    "className": "大（1）班",
    "fontSize": "",
    "fontColor": "#F0F0F0",
    "playType": 1,
    "playSpeed": 2,
    "playShow": 30,
    "openTime": "1970-01-01 10:30:00",
    "closeTime": "",
    "brightness": 80,
    "contrast": 50,
    "volume": 50,
    "createTime": "2018-05-21 13:44:46",
    "updateTime": "2018-05-21 13:46:16",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classId | string | 班级ID
className | string | 班级名称
fontSize | int | 文字大小
fontColor | string | 文字颜色
playType | int | 播放方式：1-左右滚动；2-上下滚动；3-静止；4-不显示；默认1
playSpeed | int | 播放速度，play_type为1或2时生效：1-慢速；2-中速；3-快速；默认2
playShow | int | 查看显示时间：10秒、30秒、60秒、只允许刷卡关闭（999999秒）；默认30秒
openTime | string | 开机时间，格式为“1970-01-01 10:30:00”，有效值为时间，日期为补偿字符串
closeTime | string | 关机时间，格式为“1970-01-01 10:30:00”，有效值为时间，日期为补偿字符串
brightness | int | 屏幕亮度（百分比，0到100的整数）
contrast | int | 对比度（百分比，0到100的整数）
volume | int | 音量（百分比，0到100的整数）
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询参数设置列表

```
请求地址：/setup/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
classId | false | string | 班级ID
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10011001",
        "schoolName": "中国儿童中心实验幼儿园",
        "classId": "1001100110011001",
        "className": "大（1）班",
        "fontSize": "",
        "fontColor": "#F0F0F0",
        "playType": 1,
        "playSpeed": 2,
        "playShow": 30,
        "openTime": "1970-01-01 10:30:00",
        "closeTime": "",
        "brightness": 80,
        "contrast": 50,
        "volume": 50,
        "createTime": "2018-05-21 13:44:46",
        "updateTime": "2018-05-21 13:46:16",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条参数设置”接口 ***

## 查询参数设置列表分页对象

*** 略 ***



## 添加文章

```
请求地址：/article/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
title | true | string | 标题
content | true | string | 文章内容
blockId | true | int | 班牌区块ID
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 修改文章

```
请求地址：/article/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
title | true | string | 标题
content | true | string | 文章内容
blockId | true | int | 班牌区块ID
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 删除文章

```
请求地址：/article/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一条文章

```
请求地址：/article/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10010001",
    "schoolName": "中国儿童早教基地",
    "classIds": "1001000110011002,1001000110011003",
    "classNames": "平时(2)班,平时(3)班",
    "title": "杭州下大雨",
    "publishUsername": "18790591074",
    "publishName": "系统管理员",
    "blockId": 3,
    "blockTitle": "班级窗口3",
    "createTime": "2018-05-21 20:30:00",
    "updateTime": "2018-05-23 19:02:39",
    "deleted": 0,
    "content": "<p>看见就看看水水水水水</p>",
    "beginTime": "2018-05-23 19:02:25",
    "endTime": "2018-05-24 19:03:25"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classIds | string | 班级ID，多个以逗号隔开
classNames | string | 班级名称，多个以逗号隔开
title | string | 文章标题
publishUsername | string | 发布人用户名
publishName | string | 发布人姓名
blockId | int | 默认区块ID
blockTitle | string | 默认区块名称
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是
content | string | 文章内容
beginTime | string | 展示开始时间
endTime | string | 展示结束时间


## 查询文章列表

```
请求地址：/article/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
publishUsername | false | string | 发布人用户名
title | false | string | 文章标题模糊查询
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 3,
        "schoolId": "10031002",
        "schoolName": "碧水幼儿园",
        "classIds": "1003100210011011,1003100210011007,1003100210011005,1003100210011006,1003100210011004",
        "classNames": "红蜻蜓,花蝴蝶,绿芽芽,芒果园,樱桃园",
        "title": "添加标题1111",
        "publishUsername": "18790591074",
        "publishName": "系统管理员",
        "blockId": 2,
        "blockTitle": "班级窗口2",
        "beginTime": "2018-05-22 18:00:00",
        "endTime": "2018-05-25 18:00:00",
        "createTime": "2018-05-23 18:23:53",
        "updateTime": "2018-05-24 09:41:43",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条文章”接口 ***

## 查询文章列表分页对象

*** 略 ***


## 添加图片

```
请求地址：/picture/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
titles | true | string | 多张图片的标题，以逗号","隔开
images | true | string | 多张图片的路径，以逗号","隔开
blockId | true | int | 班牌区块ID
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 修改图片

```
请求地址：/picture/{id}

请求类型：POST

请求说明：此处只修改标题和图片路径
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
title | true | string | 标题
image | true | string | 图片路径

#### 返回结果

*** 返回值为空 ***


## 删除图片

```
请求地址：/picture/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一张图片

```
请求地址：/picture/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10010001",
    "schoolName": "中国儿童早教基地",
    "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
    "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
    "title": "图片修改1",
    "image": "/upload/image1.jpg",
    "publishUsername": "18790591074",
    "publishName": "系统管理员",
    "createTime": "2018-05-22 06:24:43",
    "updateTime": "2018-05-22 06:28:38"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classIds | string | 班级ID，多个以逗号隔开
classNames | string | 班级名称，多个以逗号隔开
title | string | 文章标题
image | string | 文章内容
publishUsername | string | 发布人用户名
publishName | string | 发布人姓名
createTime | string | 创建时间
updateTime | string | 修改时间


## 查询图片列表

```
请求地址：/picture/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
publishUsername | false | string | 发布人用户名
title | false | string | 标题模糊查询
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10010001",
        "schoolName": "中国儿童早教基地",
        "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
        "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
        "title": "图片修改1",
        "image": "/upload/image1.jpg",
        "publishUsername": "18790591074",
        "publishName": "系统管理员",
        "createTime": "2018-05-22 06:24:43",
        "updateTime": "2018-05-22 06:28:38"
    }
]

```

#### 返回参数

*** 参考“查询一张图片”接口 ***

## 查询图片列表分页对象

*** 略 ***



## 添加视频

```
请求地址：/video/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
title | true | string | 视频标题
video | true | string | 视频路径
blockId | true | int | 班牌区块ID
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 修改视频

```
请求地址：/video/{id}

请求类型：POST

请求说明：此处只修改标题和路径
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
title | true | string | 标题
video | true | string | 路径

#### 返回结果

*** 返回值为空 ***


## 删除视频

```
请求地址：/video/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一个视频

```
请求地址：/video/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10010001",
    "schoolName": "中国儿童早教基地",
    "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
    "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
    "title": "视频修改1",
    "video": "/upload/video1.mp4",
    "publishUsername": "18790591074",
    "publishName": "系统管理员",
    "createTime": "2018-05-22 06:58:32",
    "updateTime": "2018-05-22 07:01:17"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classIds | string | 班级ID，多个以逗号隔开
classNames | string | 班级名称，多个以逗号隔开
title | string | 标题
video | string | 路径
publishUsername | string | 发布人用户名
publishName | string | 发布人姓名
createTime | string | 创建时间
updateTime | string | 修改时间


## 查询视频列表

```
请求地址：/video/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
publishUsername | false | string | 发布人用户名
title | false | string | 标题模糊查询
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10010001",
        "schoolName": "中国儿童早教基地",
        "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
        "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
        "title": "视频修改1",
        "video": "/upload/video1.mp4",
        "publishUsername": "18790591074",
        "publishName": "系统管理员",
        "createTime": "2018-05-22 06:58:32",
        "updateTime": "2018-05-22 07:01:17"
    }
]

```

#### 返回参数

*** 参考“查询一个视频”接口 ***

## 查询视频列表分页对象

*** 略 ***


## 查询消息列表

```
请求地址：/message/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
classId | false | string | 班级ID
senderUsername | false | string | 发送人username
receiverUsername | false | string | 接收人username
msgContent | false | string | 消息内容
readStatus | false | int | 是否已读：0-未读；1-已读；为空时查询全部
page | false | int | 页码
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10010001",
        "classId": "1001000110010002",
        "senderUsername": "1001150925154536025",
        "senderName": "安辰朗",
        "receiverUsername": "1001150925154537031",
        "receiverName": "张桐赫",
        "msgType": 1,
        "msgSource": 1,
        "readStatus": 0,
        "readTime": "",
        "createTime": "2018-05-22 10:41:42",
        "updateTime": "2018-05-22 10:41:42",
        "deleted": 0,
        "msgContent": "这是发送为班牌的文本消息"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | 菜单ID
schoolId  | string | 学校ID
classId | string | 班级ID 
senderUsername | string | 发送人username
senderName | string | 发送人姓名
receiverUsername | string | 接收人username
receiverName | string | 接收人姓名
msgType | string | 消息类型：1-文本消息；2-图片消息；默认1
msgSource | string | 消息发送平台：1-APP；2-电子班牌；默认1
readStatus | int | 是否已读：0-未读；1-已读；默认0
readTime | string | 读取时间
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是
msgContent | string | 消息内容：文本消息是文本内容，图片消息是图片路径

## 查询消息列表分页对象

*** 略 ***


## 查询展示内容列表

```
请求地址：/content-show/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
classId | true | string | 班级ID
blockId | true | int | 区块ID
page | true | int | 分页页数 
limit | true | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 2,
        "contentType": 1,
        "contentId": 1,
        "contentTitle": "杭州下大雨",
        "contentBody": "看见就看看水水水水水",
        "schoolId": "10010001",
        "schoolName": "中国儿童早教基地",
        "blockId": 3,
        "blockTitle": "班级窗口3",
        "classId": "1001000110010010",
        "className": "周六(1)班",
        "beginTime": "2018-05-21 10:30:00",
        "endTime": "2018-05-25 10:30:00",
        "createTime": "2018-05-21 20:30:00",
        "updateTime": "2018-05-21 20:30:00"
    }
]

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
contentType  | string | 内容类型：1-文章；2-相册；3-视频
contentId | string | 内容ID：对应文章、相册、视频的ID 
contentTitle | string | 内容标题
contentBody | int | 内容主体
schoolId | int | 学校ID
schoolName | string | 学校名称
blockId | string | 班牌区块ID
blockTitle | string | 区块标题
classId | string | 班级ID
className | string | 班级名称
beginTime | string | 展示开始时间
endTime | string | 展示结束时间
createTime | string | 创建时间
updateTime | string | 修改时间

## 查询展示内容列表分页对象

*** 略 ***

## 查询一条班牌运行状态信息

```
请求地址：/check/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "deviceId": 7,
    "deviceTitle": "电子班牌",
    "runStatus": 1,
    "image": "1011111.jpg",
    "styleId": 3,
    "styleTitle": "考勤模式",
    "network": "wifi",
    "ramAll": 6291456,
    "ramFree": 3000000,
    "romAll": 268435456,
    "romFree": 100100100,
    "softVersion": "2.0",
    "createTime": "2018-05-25 11:48:38",
    "updateTime": "2018-05-25 11:48:38",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
deviceId  | int | 设备ID
deviceTitle | string | 设备名称 
runStatus | int | 运行状态：1-正常；0-异常
image | string | 班牌截图
styleId | int | 当前运行模式ID
styleTitle | string | 当前运行模式名称
network | string | 网络模式
ramAll | int | 班牌内存，单位：KB
ramFree | int | 可用内存，单位：KB
romAll | int | 班牌存储，单位：KB
romFree | int | 可用存储，单位：KB
softVersion | string | 班牌软件版本
createTime | string | 创建时间
updateTime | string | 修改时间


## 查询班牌运行状态列表

```
请求地址：/check/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceSN | false | string | 班牌唯一编号
runStatus | false | int | 运行状态：1-正常；0-异常

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "deviceId": 7,
        "deviceTitle": "电子班牌",
        "runStatus": 1,
        "image": "1011111.jpg",
        "styleId": 3,
        "styleTitle": "考勤模式",
        "network": "wifi",
        "ramAll": 6291456,
        "ramFree": 3000000,
        "romAll": 268435456,
        "romFree": 100100100,
        "softVersion": "2.0",
        "createTime": "2018-05-25 11:48:38",
        "updateTime": "2018-05-25 11:48:38",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条班牌运行状态信息”接口 ***

## 查询班牌运行状态列表分页对象

*** 略 ***



## 添加课程

```
请求地址：/course/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID
teacherId | true | string | 教师id
title | true | string | 课程名称 
active | true | int | 是否正在开课：0-否；1-是；默认1
intro | false | string | 课程介绍
yearNum | false | int | 开课年份
term | false | int | 开课学期


#### 返回结果

*** 返回值为空 ***


## 修改课程

```
请求地址：/course/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
schoolId | true | string | 学校ID
teacherId | true | string | 教师id
title | true | string | 课程名称 
active | true | int | 是否正在开课：0-否；1-是；默认1
intro | false | string | 课程介绍
yearNum | false | int | 开课年份
term | false | int | 开课学期

#### 返回结果

*** 返回值为空 ***


## 删除课程

```
请求地址：/course/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一个课程

```
请求地址：/course/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "title": "初三物理三班",
    "intro": "物理课程1111",
    "active": 1,
    "teacherId": "16065009105413921",
    "teacherName": "梁静静",
    "yearNum": 2018,
    "term": 2,
    "schoolId": "10011001",
    "schoolName": "中国儿童中心实验幼儿园",
    "createTime": "2018-05-26 12:35:54",
    "updateTime": "2018-05-26 12:44:45",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
title  | string | 课程名称
intro | string | 课程介绍 
active | int | 是否正在开课：0-否；1-是；默认1
teacherId | string | 教师id
teacherName | string | 教师姓名
yearNum | int | 开课年份
term | int | 开课学期
schoolId | string | 学校ID
schoolName | string | 学校名称
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是


## 查询课程列表

```
请求地址：/course/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
title | false | string | 课程名称模糊查询
teacherName | false | string | 课程教师姓名
schoolId | false | string | 学校ID
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "title": "初三物理三班",
        "intro": "物理课程1111",
        "active": 1,
        "teacherId": "16065009105413921",
        "teacherName": "梁静静",
        "yearNum": 2018,
        "term": 2,
        "schoolId": "10011001",
        "schoolName": "中国儿童中心实验幼儿园",
        "createTime": "2018-05-26 12:35:54",
        "updateTime": "2018-05-26 12:44:45",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一个课程”接口 ***

## 查询课程列表分页对象

*** 略 ***


## 调整班级学生

```
请求地址：/course/student/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
courseId | true | int | 课程ID
studentIds | true | string | 课程下所有学生ID，以逗号隔开

#### 返回结果

*** 返回值为空 ***



## 添加课表

```
请求地址：/curriculum/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
week | true | int | 星期几，有效值为1到7 
orderNumber | true | int | 第几节课，有效值为1到12
beginTime | true | string | 开始时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
endTime | true | string | 结束时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
courseId | true | int | 课程ID
classId | true | string | 班级ID
schoolId | true | string | 学校ID

#### 返回结果

*** 返回值为空 ***


## 修改课表

```
请求地址：/curriculum/{id}

请求类型：POST
```

#### 请求参数
字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
week | true | int | 星期几，有效值为1到7 
orderNumber | true | int | 第几节课，有效值为1到12
beginTime | true | string | 开始时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
endTime | true | string | 结束时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
courseId | true | int | 课程ID
classId | true | string | 班级ID
schoolId | true | string | 学校ID

#### 返回结果

*** 返回值为空 ***


## 删除课表

```
请求地址：/curriculum/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一条课表

```
请求地址：/curriculum/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "week": 1,
    "orderNumber": 2,
    "beginTime": "1970-01-01 10:00:00",
    "endTime": "1970-01-01 10:40:00",
    "courseId": 1,
    "courseTitle": "初三物理三班",
    "courseTeacher": "梁静静",
    "classId": "1003100110011002",
    "className": "正常班级",
    "schoolId": "10031001",
    "schoolName": "媒成科技有限公司",
    "createTime": "2018-05-28 12:18:01",
    "updateTime": "2018-05-28 12:36:38",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
week  | int | 星期几，有效值为1到7
orderNumber | int | 第几节课，有效值为1到12 
beginTime | string | 开始时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
endTime | string | 结束时间，格式为“1970-01-01 10:00:00”，有效值为时间，日期为补偿字符串
courseId | int | 课程ID
courseTitle | string | 课程标题
courseTeacher | string | 课程教师
classId | string | 班级ID
className | string | 班级名称
schoolId | string | 学校ID
schoolName | string | 学校名称
createTime | string | 创建时间
updateTime | string | 修改时间


## 查询课表列表

```
请求地址：/curriculum/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
classId | false | string | 班级ID
week | false | int | 星期几，有效值为1到7
courseId | false | int | 课程ID
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 2,
        "week": 1,
        "orderNumber": 1,
        "beginTime": "1970-01-01 10:00:00",
        "endTime": "1970-01-01 10:40:00",
        "courseId": 1,
        "courseTitle": "初三物理三班",
        "courseTeacher": "梁静静",
        "classId": "1003100110011002",
        "className": "正常班级",
        "schoolId": "10031001",
        "schoolName": "媒成科技有限公司",
        "createTime": "2018-05-28 12:35:46",
        "updateTime": "2018-05-28 12:35:46",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条课表”接口 ***

## 查询课表列表分页对象

*** 略 ***



## 查询走班考勤列表

```
请求地址：/course/sign/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
courseId | false | int | 走班课程ID
curriculumId | false | int | 走班课表ID
studentId | false | string | 学生ID
studentClassId | false | string | 学生所在物理班级ID
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 6,
        "courseId": 1,
        "curriculumId": 1,
        "studentId": "17092701111654847",
        "studentName": "何梓鑫",
        "studentClassId": "1006100410011010",
        "signTime": "1970-01-01 09:30:00",
        "signStatus": 1,
        "image": "201805240941309670.jpg",
        "createTime": "2018-05-29 11:21:02",
        "updateTime": "2018-05-29 11:36:47",
        "deleted": 0,
        "imageThumb": "http://127.0.0.1:9001/file/201805240941309670.jpg?rules=thumb"
    }
]

```

#### 返回参数
字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
courseId  | int | 走班课程ID
curriculumId | int | 走班课表ID
studentId | string | 学生ID
studentName | string | 学生姓名
studentClassId | string | 学生所在物理班级ID
signTime | string | 签到时间
signStatus | int | 签到状态：1-正常、2-迟到、3-未签到；默认3
image | string | 考勤拍照照片
createTime | string | 创建时间
updateTime | string | 修改时间
imageThumb | string | 考勤照片的缩略图路径


## 查询走班考勤列表分页对象

*** 略 ***



## 添加通知

```
请求地址：/notice/

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
content | true | string | 通知内容
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 修改通知

```
请求地址：/notice/{id}

请求类型：POST
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | 对象ID
schoolId | true | string | 学校ID 
classIds | true | string | 班级ID，多个以逗号","隔开
content | true | string | 通知内容
beginTime | false | string | 展示开始时间
endTime | false | string | 展示结束时间

#### 返回结果

*** 返回值为空 ***


## 删除通知

```
请求地址：/notice/{id}

请求类型：DELETE
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** 返回值为空 ***


## 查询一条通知

```
请求地址：/notice/{id}

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | int | ID

#### 返回结果

*** JSON示例 ***

```

{
    "id": 1,
    "schoolId": "10010001",
    "schoolName": "中国儿童早教基地",
    "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
    "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
    "content": "发送一条学校通知",
    "publishUsername": "18790591074",
    "publishName": "系统管理员",
    "beginTime": "2018-05-05 09:00:00",
    "endTime": "2018-06-09 09:00:00",
    "createTime": "2018-05-29 14:17:44",
    "updateTime": "2018-05-29 14:20:13",
    "deleted": 0
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | int | ID
schoolId  | string | 学校ID
schoolName | string | 学校名称 
classIds | string | 班级ID，多个以逗号隔开
classNames | string | 班级名称，多个以逗号隔开
content | string | 通知内容
publishUsername | string | 发布人用户名
publishName | string | 发布人姓名
beginTime | string | 展示开始时间
endTime | string | 展示结束时间
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | int | 是否删除：0-否；1-是



## 查询通知列表

```
请求地址：/notice/list

请求类型：GET
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | false | string | 学校ID
classId | false | string | 班级ID
publishUsername | false | string | 发布人用户名
content | false | string | 内容查询
page | false | int | 分页页数 
limit | false | int | 每页显示条数

#### 返回结果

*** JSON示例 ***

```

[
    {
        "id": 1,
        "schoolId": "10010001",
        "schoolName": "中国儿童早教基地",
        "classIds": "1001000110010002,1001000110010010,1001000110011001,1001000110011002",
        "classNames": "周六(2)班,周六(1)班,平时(1)班,平时(2)班",
        "content": "发送一条学校通知",
        "publishUsername": "18790591074",
        "publishName": "系统管理员",
        "beginTime": "2018-05-05 09:00:00",
        "endTime": "2018-06-09 09:00:00",
        "createTime": "2018-05-29 14:17:44",
        "updateTime": "2018-05-29 14:20:13",
        "deleted": 0
    }
]

```

#### 返回参数

*** 参考“查询一条通知”接口 ***


## 查询通知列表分页对象

*** 略 ***
