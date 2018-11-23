## EventRequest 开发协议

### Roobo 开放平台

版本：2.0.0

### 大纲

* [简介](#1-简介)
  * [一些概念](#11-一些概念)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
* [Response](#3-response)
  * [协议概览](#31-协议概览)
* [Event](#4-event)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上开发Client的EventRequest协议的详细描述。

#### 1.1 一些概念

在了解本文所描述协议之前，需要对一下概念作如下说明：

* **CloudApp** - 在[_Roobo开放平台_](https://ros.ai)上接入某种云端服务或小应用。
* **CloudDispatcher** - 用于向 CloudApp 传递请求和分发 CloudApp 返回结果的云端模块。
* **CloudClient** - 用于处理 CloudDispatcher 返回结果的设备端的执行容器。
* **TTS** - **T**ext **T**o **S**peech 的缩写，这是机器人的语音表达方式。

### 2. Request

_Request_是由CloudAppClient产生的用于向 CloudDispatcher 获取对应返回结果的请求。目前有两种类型的请求：一种是**IntentRequest**，一种是**EventRequest**。**IntentRequest** 根据语音识别和语义理解（_NLP_）的结果创建的，其中会带有（NLP）的信息。**EventRequest**是在当有某种事件发生时产生的，通过_CloudAppClient_转发给当前的_CloudApp_，比如互动游戏中用户5秒无任何输入会产生一个超时事件，当前的_CloudApp_可以选择处理或者不处理。

#### 2.1 协议概览

**_Request_ 的整体协议定义如下所示：**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| clientId | string | 设备id | true |
| agentId | string | Access Key | true |
| token | string | Token | true |
| event | Object | 事件对象，包含事件名和事件相关定义 | true |
| state | Object | 设备状态 | false |

```
{
    "clientId":"1015000000000093",
    "agentId":"Your Access Key",
    "token":"Your Token",
    "state":{
       "service":"OrderCoffee",
    },
    "event":{
        "name":"AddAction",
        "params":{
           //事件参数
        }
    }
}
```

**event Object**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | true |
| params | object | 事件参数 | false |

### 3. Response

根据之前的描述，Response是 _CloudApp_ 向客户端的返回结果。

#### 3.1 协议概览

_Response_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| status | Status 对象 | [Status](status.md) | Required |
| instructions | instruction 数组 | 音频url | Optional |
| result | Result 对象 | [Result](rosai-skills-development-protocol.md#results-array) | Optional |


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
