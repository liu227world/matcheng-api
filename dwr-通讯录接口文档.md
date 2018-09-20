# 通知模块接口

*	接口使用dwr方式

## 测试地址
```
js引用：
<script type="text/javascript" src="http://www.wojiaxiaozhu.cn/mecwish/dwr/interface/ContactsService.js"></script>
<script type="text/javascript" src="http://www.wojiaxiaozhu.cn/mecwish/dwr/engine.js"></script>
跨域设置：
DWREngine.setMethod(DWREngine.ScriptTag);
ContactsService._path = 'http://www.wojiaxiaozhu.cn/mecwish/dwr';

```

## 目录

*   [根据部门查询部门成员](#根据部门查询部门成员)
*   [查询教师列表](#查询教师列表)
*   [查询我所在班级的列表](#查询我所在班级的列表)
*   [查询我所在班级的教师列表](#查询我所在班级的教师列表)
*   [查询组织下的所有教职工](#查询组织下的所有教职工)


## 根据部门查询部门成员

```

var deptCode = '227759e50fbb4e99aab6c7a46b260f2c';

ContactsService.getUsersByDepartment(deptCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deptCode | true | string | 部门code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | EmployeeId
field2 | string | EmployeeCode
field3 | string | 成员编号
field4 | string | 姓名
field5 | string | 职务
field6 | string | 加入时间
field7 | string | 用户名
field8 | string | 邮箱
field9 | string | 手机号
field10 | string | 是否启用：1-启用；0-不启用
field11 | string | 主页
field12 | string | 用户code
field13 | string | 用户param1（短号）
field14 | string | 用户param2（工作号码）
field15 | string | 用户param3



## 查询教师列表

```

var userCode = '580';

ContactsService.getTeachers(userCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
userCode | true | string | 用户code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | 部门id
field2 | string | 部门code
field3 | string | 部门名称
field4 | string | 部门说明
field5 | string | 关联班级名称
field6 | string | 状态
field7 | string | 部门类型：0-学生班级；1-教师部门
field8 | string | 组织code
field9 | string | 组织名称
field10 | string | 组织+部门名称
field11 | string | 部门排序（按正序排序）



## 查询我所在班级的列表

```

var userCode = '580';

ContactsService.getTeachers(userCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
userCode | true | string | 用户code



## 查询我所在班级的教师列表

```

var userCode = '580';

ContactsService.getTeachersByUser(userCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
userCode | true | string | 用户code

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | EmployeeId
field2 | string | EmployeeCode
field3 | string | 成员编号
field4 | string | 姓名
field5 | string | 职务
field6 | string | 加入时间
field7 | string | 用户名
field8 | string | 邮箱
field9 | string | 手机号
field10 | string | 是否启用：1-启用；0-不启用
field11 | string | 主页
field12 | string | 用户code
field13 | string | 用户param1（短号）
field14 | string | 用户param2（工作号码）
field15 | string | 用户param3


## 查询组织下的所有教职工

```
var orgCode = 'aa3533f514c049bf868849718b9b9844'
ContactsService.getTeachersByOrg(orgCode,function(res){
    console.info( res );
});

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
orgCode | true | string | 组织code


#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
field1 | string | EmployeeId
field2 | string | EmployeeCode
field3 | string | 成员编号
field4 | string | 姓名
field5 | string | 职务
field6 | string | 加入时间
field7 | string | 用户名
field8 | string | 邮箱
field9 | string | 手机号
field10 | string | 是否启用：1-启用；0-不启用
field11 | string | 主页
field12 | string | 用户code
field13 | string | 用户param1（短号）
field14 | string | 用户param2（工作号码）
field15 | string | 用户param3