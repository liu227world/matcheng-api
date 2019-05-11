
# 请假单系统接口

* 接口文档地址：http://120.27.239.166:9002/swagger-ui.html#/

* 人脸下载</v1/face/school/{schoolId}>，返回的图片需要在阿里云OSS上下载，参考：https://help.aliyun.com/document_detail/32048.html?spm=a2c4g.11186623.6.1005.16f06c375G9HQt

```
    private static String END_POINT         = "oss-cn-hangzhou.aliyuncs.com";
    private static String ACCESS_KEY_ID     = "LTAIjYrPbnYDXDYj";
    private static String ACCESS_KEY_SECRET = "VjaaVSURMm3FIJDdnnjWbnOnTwUJj0";
    private static String BUCKET_NAME       = "school-oss";
    //文件存储目录
    private static String FILE_DIR           = "upload/";
    
    图片预览地址：
https://school-oss.oss-cn-hangzhou.aliyuncs.com/upload/201904020804404830.png?x-oss-process=style/original

```

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

#### 接收参数（JSON格式的字符串，需要自行转换为JSON格式）

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
code | true | int | 错误码：0-执行成功；1-接收后台推送的消息；其它值-失败
msg | true | string | 错误说明
data | false | object | 后台发送的数据


##### data

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
sn | true | string | 设备编号
control | false | string | 人脸识别阈值
brightness | false | int | 屏幕亮度，可选值为0到100的整数
loudness | false | int | 音量，可选值为0到100的整数
title | string | 设备名称
category | int | 设备类型：1-离校终端；2-入校终端
check | int | 主动检查设备信息(当值为1时，立刻提交一次设备检查)：1-是；0-否
faces | false | Array | 学生人脸更新信息：见参数faces


##### faces

字段   |   是否必选    |   字段类型   |字段说明
------  |  -----------|-------------|-----------
uid | true | int | 学生ID
type | true | string | 更新方式，可选值：add-添加；delete-删除
image | true | string | 下载或删除的文件名称

