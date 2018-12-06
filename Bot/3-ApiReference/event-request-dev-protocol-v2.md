## 事件请求开发协议

版本：2.0.0

### 大纲

* [简介](#1-简介)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
  * [Event定义](#22-event-定义)
  * [Event命名规范](#23-命名规范)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上开发事件请求开发协议的详细描述。在当有某种事件发生时产生的，将事件转发给云端的AI策略引擎进行计算。

### 2. Request

#### 2.1 协议概览

_Request_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| agentId | String | Access Key | Required |
| token | String | Token | Required |
| sessionId | String | 会话id，如果有clientIId，一般同clientId即可 | Required |
| events | [Event](#22-event-定义) | 事件列表 | Required |
| clientId | String | 设备id | Optional |
| lang | Lang | 语种，默认"zh" | Optional |
| contexts | Context 对象 | 上文 | Optional |
| location | Location 对象 | 地理位置 | Optional |

```
{
    "agentId": "Your Access Key",
    "token": "Your Token",
    "sessionId": "sn1234567890",
    "clientId": "sn1234567890",
    "lang": "zh",
    "contexts": [
        {
            "context": "coffee",
            "service": "OrderCoffee",
            "parameters": {
                "contactId": {
                    "orgin":null,
                    "normType":"String",
                    "norm":"1486539416366"
                }
            }
        }
    ],
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
    "events": [
        {
            "name": "事件名",
            "parameters": {
                // 事件参数
            }
        }
    ],
}
```

#### 2.2 Event 定义

__Event__ 向所请求的CloudApp提供了当前的发生的事件信息，包含事件名和事件参数

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | true |
| parameters | Map | 事件参数 | true |

#### 2.3 Event 命名规范

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
