
# 电子班牌接口

*   测试接口地址：http://192.168.1.94:9002/services/BPService?wsdl

## 目录

*   [检测设备编号是否存在](#检测设备编号是否存在)
*   [获取设备基础信息](#获取设备基础信息)


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




