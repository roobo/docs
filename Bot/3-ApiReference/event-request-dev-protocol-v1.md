## EventRequest 开发协议

### Roobo 开放平台

版本：1.0.1（已停止升级）

### 大纲

* [简介](#1-简介)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
* [Response](#3-response)
  * [协议概览](#31-协议概览)
* [Event](#4-event)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上开发事件请求开发协议的详细描述。在当有某种事件发生时产生的，将事件转发给云端的AI多模交互引擎。

### 2. Request

#### 2.1 协议概览

**_Request_ 的整体协议定义如下所示：**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| clientId | string | 设备id | true |
| agentId | string | Access Key | true |
| token | string | Token | true |
| event | Event 对象 | 事件对象，包含事件名和事件相关定义 | true |
| location | Location 对象 | 地理位置 | false |
| params | Object | 事件属性，一般用于做条件判定 | false |
```
{
    "clientId": "1015000000000093",
    "agentId": "Your Access Key",
    "token": "Your Token",
    "event": {
        "type": "dedicated",
        "name": "event.bot_enter_lesson",
        "data" : {
            "service":"AiLiveDict",
        }
    },
    "location": {
        "address": {
            "country": "中国",
            "province": "北京",
            "city": "北京",
            "detail": "北京朝阳区北苑家园121号"
        },
        "longitude": 39.9197477,
        "latitude": 116.432956
    },
    "params": {
        // 事件参数 or 槽位
        map<key, object>
    }
}
```
```
{
    "clientId": "1015000000000093",
    "agentId": "Your Access Key",
    "token": "Your Token",
    "event": {
        "type": "general"
        "name": "sys.event.camera_humanface_wakeup",
    },
    "location": {
        "address": {
            "country": "中国",
            "province": "北京",
            "city": "北京",
            "detail": "北京朝阳区北苑家园121号"
        },
        "longitude": 39.9197477,
        "latitude": 116.432956
    },
    "params": {
        "isChild": true
    }
}
```

#### 2.2 Event 定义

__Event__ 向所请求的CloudApp提供了当前的发生的事件信息，包含事件名和事件相关定义

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | true |
| type | string | 可枚举值，可选值有：<br>- dedicated: 指定Skill响应的请求 <br>- general: 通用请求 | true |
| data | object |  [data定义](#221-data定义) 当type==dedicated时，才会有这个字段，描述如下。data用来描述需要由哪个skill来接收此事件 | false |

##### 2.2.1 data定义

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| service | string | skill name | true |


#### 2.3 Location 定义

__Location__ 向所请求的CloudApp提供了当前的设备的地理信息，用于帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。期望key 统一为 location

| Name | Type | Description | Required |
|--|--|--|--|
|address|object| [address定义](#231-address定义)| Optional |
|longitude|float|经度| Required |
|latitude|float|纬度| Required |


##### 2.3.1 address定义

| Name | Type | Description | Required |
|--|--|--|--|
|country|String| 国家| Optional |
|province|String| 所在地区的省份 | Optional |
|city|String|所在的城市| Optional |
|detail|String|详细的地址信息| Optional |


### 3. Response

根据之前的描述，Response是 _CloudApp_ 向客户端的返回结果。

#### 3.1 协议概览

_Response_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| status | Status 对象 | [Status](status.md) | Required |
| instructions | instruction 数组 | 音频url | Optional |
| result | Result 对象 | [Result](skill-dev-protocol.md#results-array) | Optional |


```
{
    "reqId": "AyOGE5MDJlMDk1MW-1015000000000058-1531997724913258858",
    "status": {
        "code": 0
    },
    "results": [
        {
            "hint": "小朋友，我在等你哦，快来吧",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，我在等你哦，快来吧"
                    }
                ]
            }
        }
    ]
}
```

legacy response (deprecated)
```
{
    "status": {
        "code": 0,
        "errorType": "success"
    },
    "instructions": [
        {
            "name": "",
            "url": "http://bj-voice.roo.bo/static/usertts/2018-01-17/897/reply.WmyunGaoWF.42d8df1d-c944-47d4-b657-6d5a79d1738a.mp3"
        },
        {
            "name": "",
            "url": "http://dwn.roo.bo//resource/20170411/742d84a7c68403e8034de36b46930299.mp3"
        }
    ],
    "results": [
        {
          "outputSpeech": {
            "items": [
                {
                    "type": "Audio",
                    "source": "http://bj-voice.roo.bo/static/usertts/2018-01-17/897/reply.WmyunGaoWF.42d8df1d-c944-47d4-b657-6d5a79d1738a.mp3"
                },
                {
                    "type": "Audio",
                    "source": "http://dwn.roo.bo//resource/20170411/742d84a7c68403e8034de36b46930299.mp3"
                }
            ]
          }
        }
    ]
}
```

### 4. Event

| 事件名称 | 事件含义 | 参数 | 举例 | deprecated |
| --- | --- | --- | --- | --- |
| sys.event.device_power_on  | 开机 | | | PowerOnEvent |
| sys.event.device_idle | 设备空闲 | | | IdleEvent |
| sys.event.bot_enter | 进入场景 |  | | ROSAI.EnterEvent |
| sys.event.camera_humanface_wakeup | 人脸唤醒 | "params": {<br>&nbsp;&nbsp;"isChild": bool //是否是小孩<br>&nbsp;&nbsp;"userId":string //userId<br>} | | DeviceHumanFaceEvent |
| sys.event.voice_wakeup | 语音唤醒 |  | | DeviceWakeUpBotEvent |
| sys.event.screen_touch_item | 触摸交互元素 | "params": {<br>&nbsp;&nbsp;"url": string //被交互元素url标识<br>} | | ROSAI.TouchEvent |
| event.screen_touch_5_times | 触摸5次 |  | | Touch5Times |
| sys.event.cloud_query | 云端query事件 |  | | CloudBotEvent |
