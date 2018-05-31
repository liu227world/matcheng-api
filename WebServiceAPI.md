
# 电子班牌接口

*   测试接口地址：http://192.168.1.94:9002/services/BPService?wsdl

## 目录

*   [检测设备编号是否存在](#检测设备编号是否存在)
*   [获取设备基础信息](#获取设备基础信息)


*   [内容发布（文章、图片、视频）](#内容发布（文章、图片、视频）)
*   [我发布的内容列表（文章、图片、视频）](#我发布的内容列表（文章、图片、视频）)


*   [今日走班课表](#今日走班课表)





## 检测设备编号是否存在

```
请求方式：execute("DzbpDeviceInfo","checkNumberService","deviceNumber=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 设备唯一编号 

#### 返回结果

*** JSON示例 ***

```

{
    "returnCode": "000", 
    "checkNumber": [
        {
            "RESULT": "1"
        }
    ]
}

```

#### 返回参数 checkNumber

字段    |   字段类型   |字段说明
-----------|-------------|-----------
RESULT | string | 绑定情况：0-不存在该设备编号；1-已绑定；2-未绑定


## 获取设备基础信息

```
请求方式：execute("DzbpDeviceInfo","selectDeviceInfoService","deviceNumber=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 设备唯一编号 

#### 返回结果

*** JSON示例 ***

```

{
    "returnCode": "000", 
    "selectInfoType": [
        {
            "TYPENAME": "班级窗口1", 
            "TIMES": "", 
            "PARENTID": "", 
            "TYPEID": "1"
        }, 
        {
            "TYPENAME": "班级窗口2", 
            "TIMES": "", 
            "PARENTID": "", 
            "TYPEID": "2"
        }, 
        {
            "TYPENAME": "班级窗口3", 
            "TIMES": "", 
            "PARENTID": "", 
            "TYPEID": "3"
        }, 
        {
            "TYPENAME": "公告", 
            "TIMES": "", 
            "PARENTID": "", 
            "TYPEID": "4"
        }
    ], 
    "selectTemplateInfo": [ ], 
    "selectClassInfo": [
        {
            "HEADTEACHER": "杨小拉", 
            "LOGO": "", 
            "CLASSID": "1003100110011002", 
            "SLOGAN": "", 
            "REMARK": "", 
            "CLASSNAME": "正常班级"
        }
    ], 
    "selectDeviceInfo": [
        {
            "DEVICETYPE": "1", 
            "playSpeed": 2, 
            "fontColor": "#00B0F0", 
            "COMPANYNAME": "", 
            "TENANTID": "", 
            "playType": 1, 
            "fontSize": 60, 
            "contrast": 60, 
            "brightness": 60, 
            "OFFTIME": "19:30", 
            "DEVICENAME": "电子班牌", 
            "SELFIETIMES": "06:30-23:30", 
            "DEVICENUMBER": "100011000", 
            "ONTIME": "07:30", 
            "volume": 60, 
            "playShow": 30
        }
    ]
}

```

#### 返回参数 selectInfoType
字段    |   字段类型   |字段说明
-----------|-------------|-----------
TYPEID | string | 区块ID
TYPENAME | string | 区块名称
TIMES | string | 显示时段（无效）
PARENTID | string | 上级类型ID（无效）

#### 返回参数 selectTemplateInfo 无效

#### 返回参数 selectClassInfo 
字段    |   字段类型   |字段说明
-----------|-------------|-----------
CLASSID | string | 班级ID
CLASSNAME | string | 班级名称
LOGO | string | logo
SLOGAN | string | 口号
REMARK | string | 说明
HEADTEACHER | string | 班主任姓名

#### 返回参数 selectDeviceInfo 
字段    |   字段类型   |字段说明
-----------|-------------|-----------
DEVICENUMBER | string | 设备编号
DEVICENAME | string | 设备名称
DEVICETYPE | string | 设备类型：1-班级班牌
ONTIME | string | 开机时间
OFFTIME | string | 关机时间
SELFIETIMES | string | 自拍时间段（无效）
TENANTID | string | 集团ID（空字符串）
COMPANYNAME | string | 集团名称（空字符串）
fontSize | int | 家长留言文字大小
fontColor | int | 家长留言文字颜色
playType | int | 家长留言播放方式：1-左右滚动；2-上下滚动；3-静止；4-不显示；默认1
playSpeed | int | 家长留言播放速度，play_type为1或2时生效：1-慢速；2-中速；3-快速；默认2
playShow | int | 家长留言查看显示时间：10秒、30秒、60秒、只允许刷卡关闭（999999秒）；默认30秒
brightness | int | 屏幕亮度（百分比，0到100的整数）
contrast | int | 对比度（百分比，0到100的整数）
volume | int | 音量（百分比，0到100的整数）



## 内容发布（文章、图片、视频）

```
请求方式：execute("DzbpNewsInfo","insertService","contentType=;schoolId=;classId=;title=;content=;thumb=;username=;","json");

请求说明：发布图片时，可以同时发布多张图片，多个title和content以逗号“,”隔开

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
contentType | true | string | 内容类型：1-文章；2-相册；3-视频
schoolId | true | string | 学校ID 
classId | true | string | 班级ID 
title | true | string | 内容标题 
content | true | string | 文章内容，或图片文件名，或视频文件名（上传后返回的文件名） 
thumb | false | string | 发视频时有效，视频缩略图 
username | true | string | 发布人用户名

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"msg": "文章发布成功"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
msg | string | 返回值说明


## 我发布的内容列表（文章、图片、视频）

```
请求方式：execute("DzbpNewsInfo","myContentList","contentType=;username=;page=;limit=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
contentType | true | int | 内容类型：1-文章；2-相册；3-视频，值为空时，查询全部类型
username | true | string | 用户名 
page | true | int | 第几页 
limit | true | int | 每页条数 

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"contentList": [{
		"contentBody": "http://192.168.1.10:9000/file/201805281116122383.png?rules=normal",
		"createTime": "2018-05-28 11:16:38",
		"schoolName": "富阳区银湖街道受降幼儿园",
		"publishName": "系统管理员",
		"updateTime": "2018-05-28 11:16:38",
		"classId": "1006100910051018",
		"contentThumb": "http://192.168.1.10:9000/file/201805281116122383.png?rules=thumb",
		"publishUsername": "18790591074",
		"beginTime": "2018-05-28 11:16:25",
		"contentType": 2,
		"endTime": "2018-05-29 11:17:25",
		"deleted": 0,
		"contentId": 41,
		"id": 110,
		"blockTitle": "公告",
		"blockId": 4,
		"contentTitle": "萌萌02.png",
		"className": "小一班",
		"schoolId": "10061009"
	}]
}

```

#### 返回参数 contentList
*** 参数未按照返回json排序 ***

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | string | ID
contentType | string | 内容类型：1-文章；2-相册；3-视频
contentId | string | 内容ID：对应文章、相册、视频的ID
contentTitle | string | 内容标题
schoolId | string | 学校ID
schoolName | string | 学校名称
blockId | string | 班牌区块ID
blockTitle | string | 区块标题
classId | string | 班级ID
className | string | 班级名称
publishUsername | string | 发布人username
publishName string | 发布人姓名
beginTime | string | 展示开始时间
endTime | string | 展示结束时间
createTime | string | 创建时间
updateTime | string | 修改时间
deleted | string | 是否删除：0-否；1-是
contentBody | string | 内容体：文章内容，或图片原图路径，或视频路径
contentThumb | string | 内容缩略图：类型为图片或视频时有效



## 今日走班课表

```
请求方式：execute("DzbpCourseInfo","selectCdCourseService","classId=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
classId | true | string | 班级ID

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"selectCdCourse": [{
		"startTime": "10:00",
		"codeName": "初三物理三班",
		"weekDay": 4,
		"classId": "1003100110011002",
		"orderNumber": 1,
		"img": "",
		"endTime": "10:40",
		"teacherName": "梁静静",
		"teacherId": ""
	}]
}

```

#### 返回参数 selectCdCourse

字段    |   字段类型   |字段说明
-----------|-------------|-----------
startTime | string | 课程开始时间
codeName | string | 课程名称
weekDay | string | 星期几：1到7
classId | string | 班级ID
orderNumber | string | 第几节课
img | string | 课程图标（无数据）
endTime | string | 课程结束时间
teacherName | string | 教师姓名
teacherId | string | 教师username（值为空）


## 当前课程和学生列表：正在上课或半小时内开始上课

```
请求方式：execute("DzbpCourseInfo","selectCourseStuService","classId=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
classId | true | string | 班级ID

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"selectStuList": [{
		"startTime": "2018-05-29 09:20:00",
		"cardId": "3566229324",
		"studentId": "17092701111654847",
		"studentName": "何梓鑫"
	}],
	"selectLeaveList": []
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
startTime | string | 考勤时间
cardId | string | 学生卡号
studentId | string | 学生ID
studentName | string | 学生姓名


## 走班刷卡考勤

```
请求方式：execute("DzbpCourseInfo","signService","classId=;cardId=;image=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
classId | true | string | 班级ID
cardId | true | string | 签到卡号
image | true | string | 上传的签到图片名

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"msg": "签到成功"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
msg | string | 签到说明


