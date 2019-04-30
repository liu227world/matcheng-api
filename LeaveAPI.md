
# 请假单系统接口

*   测试接口地址：
*   正式接口地址：

## 门房终端接口目录

*   [设备绑定并返回配置信息](#设备绑定并返回配置信息)
*   [设备参数设置](#设备参数设置)
*   [设备检查长连接](#设备检查长连接)
*   [全量更新学生和人脸](#全量更新学生和人脸)
*   [查询离校信息并修改状态](#查询离校信息并修改状态)
*   [查询入校信息并修改状态](#查询入校信息并修改状态)


## 微信小程序接口目录

*** 待补充 ***



## 接口异常错误说明

*** 500 JSON示例 ***

```
{
    "code":1001,
    "msg":"错误信息",
    "data":""
}
```


## 设备绑定并返回配置信息

```
请求地址：/v1/device/bind

请求类型：POST

请求类型：JSON

请求说明：
1、验证设备是否可用；
2、查询设备基本信息；
3、初始化配置
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | string | 设备唯一编号 
version | false | string | 软件版本号

#### 返回结果

*** JSON示例 ***

```
{
    "sn": "10000006",
    "title": "演示学校南门离校终端",
    "intro": "设备说明信息",
    "category": 1,
    "schoolId": 1,
    "place": "学校南门",
    "control": "0.8",
    "brightness": 80,
    "loudness": 80,
    "run": 1,
    "version": "1.0.0"
}
```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
sn | string | 设备编号：用于设备的验证和绑定
title | string | 设备名称
intro | string | 设备说明
category | int | 设备类型：1-离校终端；2-入校终端
schoolId | int | 学校ID
place | string | 安装位置
control | string | 人脸识别阈值
brightness | int | 屏幕亮度，可选值为0到100的整数
loudness | int | 音量，可选值为0到100的整数
run | int | 运行状态：1-正常；0-异常
version | string | 软件版本号


## 设备参数设置

```
请求地址：/v1/device/setting

请求类型：POST

请求类型：JSON

请求说明：
设置设备亮度和音量
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | string | 设备唯一编号 
brightness | true | int | 屏幕亮度，可选值为0到100的整数
loudness | true | int | 音量，可选值为0到100的整数

#### 返回结果

*** 空 ***


## 设备检查长连接

```
请求地址：/v1/device/check

请求类型：WebSocket

请求说明：
上传设备运行状态，接收后台的推送信息

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | string | 设备编号
run | int | 运行状态：1-正常；0-异常
network | false | string | 网络模式
cpu | false | string | cpu占用率
ramAll | false | int | 设备内存，单位：Byte
ramFree | false | int | 可用内存，单位：Byte
romAll | false | int | 设备存储，单位：Byte
romFree | false | int | 可用存储，单位：Byte

#### 接收参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | string | 设备编号
control | false | string | 人脸识别阈值
brightness | false | int | 屏幕亮度，可选值为0到100的整数
loudness | false | int | 音量，可选值为0到100的整数
title | string | 设备名称
category | int | 设备类型：1-离校终端；2-入校终端
check | int | 主动检查设备信息：1-是；0-否
faces | false | Array | 学生人脸更新信息：见参数faces

##### faces

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
studentId | true | int | 学生ID
type | true | string | 更新方式，可选值：add-添加；delete-删除
image | true | string | 图片（下载地址或删除的文件名称）



## 全量更新学生和人脸

```
请求地址：/v1/faces/school/{schoolId}

请求类型：GET

请求说明：
根据学校ID查询并下载全部学生的人脸信息
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
schoolId | true | int | 学校ID 

#### 返回结果

*** JSON示例 ***

```
[
    {
        "sno": "20190001",
        "nickname": "李某某同学",
        "faces": ["https://image1.jpg","https://image2.jpg"]
    }
]
```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
sno | string | 学生编号
nickname | string | 学生姓名
faces | string | 人脸照片下载地址列表


## 查询离校信息并修改状态

```
请求地址：/v1/leave

请求类型：POST

请求说明：
查询一个学生的请假单信息，并修改离校状态
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | int | 设备编号  
sno | false | string | 学生编号，刷脸数据，和 cno 二选一 
cno | false | string | 学生卡号，刷卡数据，和 sno 二选一

#### 返回结果

*** JSON示例 ***

```
{
    "code": 1,
    "msg": "XXX请假离校，请放行",
    "data": {
        "sno": "20190001",
        "nickname": "李某某同学",
        "avatar": "https://image.jpg",
        "startTime": "2019-10-10 10:10",
        "endTime": "2019-10-11 10:10",
        "state": 3,
        "classId": 1,
        "className": "一年级（一）班",
        "gradeId": 1,
        "gradeName": "一年级",
        "schoolId": 1,
        "schoolName": "演示学校",
        "message": "2019-09-11 12:00 XX班XX同学请假离校"
    }
}
```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
code | string | 学生编号
msg | string | 提示消息，需要语音合成并播报
data | string | 请假单信息，见参数data

#### data

字段    |   字段类型   |字段说明
-----------|-------------|-----------
sno | string | 学生编号
nickname | string | 学生姓名
avatar | string | 学生照片
startTime | string | 请假开始时间
endTime | string | 请假结束时间
state | string | 请假单状态：1-待班主任审批；2-待学生处审批；3-已请假未离校；4-已离校未销假；5-已销假
classId | string | 班级ID
className | string | 班级名称
gradeId | string | 年级ID
gradeName | string | 年级名称
schoolId | string | 学校ID
schoolName | string | 学校名称
message | string | 请假文字说明


## 查询入校信息并修改状态

```
请求地址：/v1/enter

请求类型：POST

请求说明：
查询一个学生的请假单信息，并修改入校状态
```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | int | 设备编号
sno | false | string | 学生编号，刷脸数据，和 cno 二选一 
cno | false | string | 学生卡号，刷卡数据，和 sno 二选一

#### 返回结果

*** JSON示例 ***

```
{
    "code": 1,
    "msg": "XXX请假离校，请放行",
    "data": {
        "sno": "20190001",
        "nickname": "李某某同学",
        "avatar": "https://image.jpg",
        "startTime": "2019-10-10 10:10",
        "endTime": "2019-10-11 10:10",
        "state": 3,
        "classId": 1,
        "className": "一年级（一）班",
        "gradeId": 1,
        "gradeName": "一年级",
        "schoolId": 1,
        "schoolName": "演示学校",
        "message": "2019-09-11 12:00 XX班XX同学请假离校"
    }
}
```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
code | string | 学生编号
msg | string | 提示消息，需要语音合成并播报
data | string | 请假单信息，见参数data

#### data

字段    |   字段类型   |字段说明
-----------|-------------|-----------
sno | string | 学生编号
nickname | string | 学生姓名
avatar | string | 学生照片
startTime | string | 请假开始时间
endTime | string | 请假结束时间
state | string | 请假单状态：1-待班主任审批；2-待学生处审批；3-已请假未离校；4-已离校未销假；5-已销假
classId | string | 班级ID
className | string | 班级名称
gradeId | string | 年级ID
gradeName | string | 年级名称
schoolId | string | 学校ID
schoolName | string | 学校名称
message | string | 请假文字说明
