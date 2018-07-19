
# 电子班牌接口

*   测试接口地址：http://192.168.1.10:9002/services/BPService?wsdl
*   测试命名空间：http://service.matcheng.com

## 目录

*   [检测设备编号是否存在](#检测设备编号是否存在)
*   [获取设备基础信息](#获取设备基础信息)

*   [内容发布](#内容发布)
*   [我发布的内容列表](#我发布的内容列表)

*   [当前课程和学生列表](#当前课程和学生列表)
*   [走班刷卡考勤](#走班刷卡考勤)

*   [信息列表查询](#信息列表查询)
*   [通知列表查询](#通知列表查询)

*   [查询班级未读留言](#查询班级未读留言)
*   [刷卡查看我的未读留言](#刷卡查看我的未读留言)
*   [学生刷卡拍照](#学生刷卡拍照)

*   [添加班级考勤](#添加班级考勤)

*   [刷卡验证](#刷卡验证)
*   [根据ID查询公告内容](#根据id查询公告内容)

*   [查询班牌当前模式](#查询班牌当前模式)

*   [查询今天的班级考勤信息](#查询今天的班级考勤信息)
*   [查询班级课表](#查询班级课表)



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
	"selectInfoType": [{
		"TYPENAME": "宣传模式",
		"TIMES": "11:30-12:00",
		"PARENTID": "",
		"TYPEID": "10100001"
	}, {
		"TYPENAME": "考勤模式",
		"TIMES": "12:10-13:00",
		"PARENTID": "",
		"TYPEID": "10100002"
	}],
	"selectTemplateInfo": [],
	"selectClassInfo": [{
		"HEADTEACHER": "王蒙",
		"LOGO": "",
		"CLASSID": "1003100110011002",
		"SLOGAN": "好好学习天天向上",
		"REMARK": "测试班级",
		"CLASSNAME": "正常班级"
	}],
	"selectDeviceInfo": [{
		"DEVICETYPE": "1",
		"playSpeed": 2,
		"fontColor": "#00B0F0",
		"COMPANYNAME": "",
		"TENANTID": "",
		"playType": 1,
		"fontSize": 60,
		"brightness": 97,
		"contrast": 100,
		"OFFTIME": "19:30",
		"DEVICENAME": "电子班牌",
		"SELFIETIMES": "06:30-23:30",
		"DEVICENUMBER": "100011000",
		"ONTIME": "07:30",
		"volume": 99,
		"playShow": 30
	}]
}

```

#### 返回参数 selectInfoType
字段    |   字段类型   |字段说明
-----------|-------------|-----------
TYPEID | string | 模式ID
TYPENAME | string | 模式名称
TIMES | string | 切换显示时段
PARENTID | string | 上级类型ID

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



## 内容发布

```
请求方式：execute("DzbpNewsInfo","insertService","contentType=;schoolId=;classId=;title=;content=;thumb=;username=;blockId=;","json");

请求说明：
1、发布图片时，可以同时发布多张图片，多个title和content以逗号“,”隔开；
2、可以发布班级通知、班级相册；
3、文字发布在班级通知，有效期为 1 天；图片发布到班级主窗口，有效期为 7 天

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
contentType | true | string | 内容类型：1-班级通知；2-班级相册
schoolId | true | string | 学校ID 
classId | true | string | 班级ID 
title | true | string | 内容标题 
content | true | string | 文章内容，或图片文件名，或视频文件名（上传后返回的文件名） 
thumb | false | string | 发视频时有效，视频缩略图（暂不能发送视频，字段无效）
username | true | string | 发布人用户名
blockId | true | string | 区块ID，上传图片时有效：1-小黑板；2-班级之星；3-主窗口，默认为3

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


## 我发布的内容列表

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




## 当前课程和学生列表


```
请求方式：execute("DzbpCourseInfo","selectCourseStuService","classId=;","json");
请求说明：取当前走班课程，或半小时内开始上课的走班课程

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
	"courseInfo": [{
		"ID": 1,
		"CDID": "1003100110011002",
		"CODENAME": "高三物理一班",
		"CLASSTIME": "15:00-17:50",
		"WEEKDAY": 3,
		"ORDERNUMBER": 2,
		"TEACHERID": "17070124020620699",
		"TEACHERNAME": "杨小拉"
		"curriculumId": 2
	}],
	"selectStuList": [{
		"byCard": "0",
		"CARDID": "",
		"STUDENTIMG": "",
		"STUDENT_NAME": "周钰铠",
		"STUDENTID": "17092518095625890",
		"STARTTIME": "",
		"FIRSTTIME": "",
		"CARDNUMBER": "",
		"STUDENTNAME": "周钰铠",
		"STUDENT_ID": "17092518095625890",
		"LASTTIME": ""
	}],
	"selectLeaveList": []
}

```
#### 返回参数 courseInfo

字段    |   字段类型   |字段说明
-----------|-------------|-----------
ID | string | 课程ID
CDID | string | 场地（班级）ID
CODENAME | string | 课程名称
CLASSTIME | string | 课程时间
WEEKDAY | string | 星期几（1到7）
ORDERNUMBER | string | 第几节课
TEACHERID | string | 教师ID
TEACHERNAME | string | 教师姓名
curriculumId | int | 走班课程表ID

#### 返回参数 selectStuList

字段    |   字段类型   |字段说明
-----------|-------------|-----------
STUDENTID | string | 学生ID
STUDENTNAME | string | 学生姓名
STUDENTIMG | string | 头像路径
FIRSTTIME | string | 最早刷卡时间
LASTTIME | string | 最后刷卡时间
CARDNUMBER | string | 卡号
byCard | string | 是否刷卡：0-未刷卡；1-已刷卡
STUDENT_ID | string | 
STUDENT_NAME | string | 
STARTTIME | string | 
CARDID | string | 


## 走班刷卡考勤

```
请求方式：execute("DzbpCourseInfo","signService","classId=;cardId=;signTime=;image=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
curriculumId | true | string | 走班课表ID
cardId | true | string | 签到卡号
signTime | true | string | 考勤时间，格式为：1970-01-01 10:00:00
image | true | string | 上传的签到图片名

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"insertAttendance": [{
		"COLNUM": "1"
	}],
	"studentInfo": [{
		"studentId": "17092701111654847",
		"studentName": "何梓鑫"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
COLNUM | string | 
studentId | string | 学生ID
studentName | string | 学生姓名



## 信息列表查询

```
请求方式：execute("DzbpNewsInfo","selectInfoListService","deviceNumber=;limitStr=;infoType=;top=;","json");
请求说明：
1、返回结果为分别取四个区块的集合，如 limitStr=1,10，则四个区块分别取10条数据；
2、只取有效期内的数据

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 设备编号
limitStr | true | string | 分页参数字符串，格式为0,10
infoType | true | string | 信息类型：对应新区块ID（无效）
top | true | string | 是否置顶（无效）

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"selectInfoList": [ {
		"RESOURCEURL": "",
		"CREATEUSERNAME": "余博伦",
		"CONTENT": "http://192.168.1.10:9000/file/b.jpg?rules=normal",
		"TEXTTYPE": "2",
		"ID": "115",
		"IMGURL": "http://192.168.1.10:9000/file/b.jpg?rules=thumb",
		"CREATEUSER": "1003160811111253377",
		"CREATETIME": "2018-05-30 18:39:57",
		"DURATION": "300",
		"INFOTYPE": "3",
		"TITLE": "webservice图片",
		"EDITTIME": "2018-05-30 18:39:57"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
RESOURCEURL | string | 资源路径（无效）
CREATEUSERNAME | string | 发布人姓名
CONTENT | string | 内容：文章主体，或图片路径，或视频路径
TEXTTYPE | string | 文本类型：1-文章；2-图片；3-视频
ID | string | ID
IMGURL | string | 缩略图路径，图片或视频时有效
CREATEUSER | string | 发布人用户名
CREATETIME | string | 创建时间
DURATION | string | 显示时长（300固定值）
INFOTYPE | string | 信息类型：对应新区块ID
TITLE | string | 内容标题
EDITTIME | string | 修改时间



## 通知列表查询

```
请求方式：execute("DzbpNotice","selectNoticeListService","deviceNumber=;limitStr=;","json");
请求说明：
1、只取有效期内的数据

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 设备编号
limitStr | true | string | 分页参数字符串，格式为0,10

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"selectNoticeList": [{
		"CREATEUSERNAME": "系统管理员",
		"NOTICETITLE": "一条校内通知",
		"DATASOURCE": "",
		"CONTENT": "一条校内通知",
		"CREATETIME": "2018-05-31 18:59:51",
		"NOTICEID": "3",
		"DURATION": "300",
		"TYPE": "紧急通知",
		"TYPEID": "10002",
		"EDITTIME": "2018-05-31 18:59:51"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
CREATEUSERNAME | string | 发布人姓名
NOTICETITLE | string | 通知标题：取内容
DATASOURCE | string | （未使用）
CONTENT | string | 通知内容
CREATETIME | string | 创建时间
NOTICEID | string | 通知ID
DURATION | string | 显示时长（无效）
TYPE | string | 通知类型
TYPEID | string | 通知名称
EDITTIME | string | 修改时间



## 查询班级未读留言

```
请求方式：execute("DzbpMessage","selectMessageListService","classId=;","json");

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
	"messageList": [{
		"TIME": "2018-05-22 10:41:42",
		"CONTENT": "这是发送为班牌的文本消息",
		"STUDENTID": "1001150925154537031",
		"ID": "1",
		"PTITLE": "这是发送为班牌的文本消息",
		"PARENTID": "安辰朗",
		"ISREAD": "0",
		"STUDENTNAME": "张桐赫"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
ID | string | 留言ID
STUDENTID | string | 学生username
STUDENTNAME | string | 学生姓名
PARENTID | string | 家长username
PTITLE | string | 标题(取内容)
CONTENT | string | 内容
TIME | string | 发送时间
ISREAD | string | 是否已读：0-未读；1-已读；



## 刷卡查看我的未读留言

```
请求方式：execute("DzbpLeave","listLeaveByStudentService","cardId=;","json");
请求说明：请求成功后，留言修改为已读状态

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
cardId | true | string | 刷卡卡号

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"messageList": [{
		"TIME": "2018-05-26 16:38:48",
		"CONTENT": "测试信息",
		"STUDENTID": "2014010440",
		"ID": "15",
		"PTITLE": "测试信息",
		"PARENTID": "安辰朗",
		"ISREAD": "0",
		"STUDENTNAME": "陆亭宇"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
ID | string | 留言ID
STUDENTID | string | 学生username
STUDENTNAME | string | 学生姓名
PARENTID | string | 家长username
PTITLE | string | 标题(取内容)
CONTENT | string | 内容
TIME | string | 发送时间
ISREAD | string | 是否已读：0-未读；1-已读；


## 学生刷卡拍照

```
请求方式：execute("DzbpPhotoInfo","insertStudnetPhotoService","cardId=;image=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
cardId | true | string | 刷卡卡号
image | true | string | 上传的图片名称

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"msg": "拍照上传成功"
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
msg | string | 上传说明



## 添加班级考勤

```
请求方式：execute("DzbpAttendanceInfo","insertAttendanceService","deviceNumber=;cardId=;signTime=;image=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 设备编号
cardId | true | string | 刷卡卡号
signTime  | true | string | 考勤时间，格式为：1970-01-01 10:00:00
image | true | string | 上传的图片名称

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"msg": "考勤成功",
	"insertAttendance": [{
		"COLNUM": "1"
	}],
	"studentInfo": [{
		"studentId": "16119014055854125",
		"studentName": "舒全智"
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
COLNUM | string | 
studentId | string | 学生ID
studentName | string | 学生姓名


## 刷卡验证

```
请求方式：execute("DzbpDeviceInfo","checkCardNumberService","cardNumber=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
cardNumber | true | string | 刷卡卡号

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"checkCardNumber": [{
		"id": "1003161114175854005",
		"name": "舒全智",
		"type": 1011
	}]
}

```

#### 返回参数

字段    |   字段类型   |字段说明
-----------|-------------|-----------
id | string | 用户名
name | string | 用户姓名
type | string | 类型(1010教职工,1011学生,1012家长)


## 根据ID查询公告内容

```
请求方式：execute("DzbpAfficheInfo","afficheInfoService","id=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
id | true | string | 内容ID，来自信鸽推送

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"afficheInfo": [{
		"ID": 181,
		"TITLE": "巡更测试二维码.jpg",
		"TYPE": 2,
		"TEXT_TYPE": "1",
		"CONTENT": "http://192.168.1.94:9000/file/201806041834366607.jpg?rules=normal",
		"CREATE_TIME": "2018-06-04 18:34:43",
		"EDIT_TIME": "2018-06-04 18:34:43",
		"CREATE_USER": "18790591074",
		"CREATE_USER_NAME": "系统管理员",
		"TENANT_ID": "",
		"SCHOOL_ID": "",
		"TEXT1": "",
		"TEXT2": "",
		"TEXT3": "",
		"TEXT4": "",
		"START_TIME": "2018-06-04 18:33:32",
		"END_TIME": "2018-06-15 18:34:32",
		"BACKGROUND_IMG": "",
		"BACKGROUND_MUSIC": "",
		"ROLL_SPEED": "3",
		"ROLL_DIRECTION": "1",
		"SHOW_TEXT": "",
		"SHOW_TYPE": "",
		"TEXT_ALPHA": "",
		"PLAY_SPEED": "",
		"IS_MUTE": ""
	}],
	"resouce": [{
		"RESOURCE_URL": "http://192.168.1.94:9000/file/201806041834366607.jpg?rules=normal",
		"REMARK": "",
		"SORT": "1"
	}]
}

```

#### 返回参数

*** 略 ***


## 查询班牌当前模式

```
请求方式：execute("DzbpDeviceInfo","thisStyleService","deviceNumber=;","json");

请求说明：
1、

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
deviceNumber | true | string | 班牌编号

#### 返回结果

*** JSON示例 ***

```

{
	"returnCode": "000",
	"afficheInfo": [{
		"BACKGROUND_MUSIC": "",
		"CREATE_TIME": "2018-06-13 15:31:37",
		"IS_MUTE": "",
		"PLAY_SPEED": "",
		"TEXT_ALPHA": "",
		"ROLL_SPEED": "3",
		"CONTENT": "http://nn.wxztc.com.cn/txy/upload/banpai/normal/201806131531348208.png",
		"CREATE_USER": "18790591074",
		"ROLL_DIRECTION": "1",
		"ID": 306,
		"BACKGROUND_IMG": "",
		"TYPE": "1",
		"TEXT_TYPE": 2,
		"EDIT_TIME": "2018-06-13 15:31:37",
		"TEXT2": "",
		"TEXT1": "",
		"SCHOOL_ID": "",
		"TEXT4": "",
		"TEXT3": "",
		"START_TIME": "2018-06-13 15:31:29",
		"TENANT_ID": "",
		"CREATE_USER_NAME": "系统管理员",
		"SHOW_TYPE": "",
		"END_TIME": "2018-06-29 15:32:29",
		"SHOW_TEXT": "",
		"TITLE": "ic_defaults_img"
	}],
	"thisStyleList": [{
		"styleName": "公告模式",
		"styleId": "1",
		"contentType": 2
	}],
	"resource": [{
		"SORT": "1",
		"RESOURCE_URL": "http://nn.wxztc.com.cn/txy/upload/banpai/normal/201806131531348208.png",
		"REMARK": ""
	}]
}

```

#### 返回参数 thisStyleList

字段    |   字段类型   |字段说明
-----------|-------------|-----------
styleId | string | 模式id：1-公告模式；4-走班模式；10100001-班级模式；10100002-考勤模式
styleName | string | 模式名称
contentType | string | 公告类型，在公告模式下有效：1-文章；2-图片

*** 其他参数略 ***



## 查询今天的班级考勤信息

```
请求方式：execute("DzbpAttendanceInfo","selectAttendanceListService","classId=;","json");

```

#### 请求参数

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
classId | true | string | 教学班级ID

#### 返回结果

*** JSON示例 ***

```

{
    "returnCode": "000",
    "selectAttendanceList": [{
        "STUDENTID": "1003170227105333596",
        "STUDENTNAME": "阿拉丁",
        "FIRSTTIME": "",
        "LASTTIME": ""
    }],
    "selectLeaveList": []
}

```

#### 返回参数 selectAttendanceList

字段    |   字段类型   |字段说明
-----------|-------------|-----------
STUDENTID | string | 学生用户名
STUDENTNAME | string | 学生姓名
FIRSTTIME | string | 当天第一次刷卡时间
LASTTIME | string | 当天最后一次刷卡时间


## 查询班级课表

```
请求方式：execute("DzbpDeviceInfo","selectClassCourseService","classId=;","json");

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
        "CODENAME": "语文",
        "ORDERNUMBER": "1",
        "TEACHERID": "17757975912",
        "TEACHERNAME": "吕鑫华",
        "WEEK_DAY": "周一",
        "CLASSID": "1003100110011002",
        "STARTTIME": "08:00",
        "ENDTIME": "08:45",
        "IMG": "icon_11.png",
        "type": "2",
        "curriculumId": "2"
    }]
}

```

#### 返回参数 selectCdCourse

字段    |   字段类型   |字段说明
-----------|-------------|-----------
CODENAME | string | 课程名称
WEEK_DAY | string | 星期几
CLASSID | string | 班级ID
ORDERNUMBER | string | 第几节课
TEACHERNAME | string | 教师姓名
TEACHERID | string | 教师username
STARTTIME | string | 开始时间
ENDTIME | string | 结束时间
IMG | string | 课程图标
type | string | 课程类型：1-教学班级课表；2-走班课表
curriculumId | string | 课表ID

