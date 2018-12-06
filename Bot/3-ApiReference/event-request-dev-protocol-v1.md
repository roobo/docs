## EventRequest 开发协议

### Roobo 开放平台

版本：1.0.1 （已停止升级）

### 大纲

* [简介](#1-简介)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
* [Response](#3-response)
  * [协议概览](#31-协议概览)
* [Event](#4-event)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上开发事件请求开发协议的详细描述。在当有某种事件发生时产生的，将事件转发给云端的AI策略引擎进行计算。

### 2. Request

#### 2.1 协议概览

**_Request_ 的整体协议定义如下所示：**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| clientId | string | 设备id | true |
| agentId | string | Access Key | true |
| token | string | Token | true |
| event | Object | 事件对象，包含事件名和事件相关定义 | true |
| params | Object | 事件属性，一般用于做条件判定 | false |

```
{
    "clientId": "1015000000000093",
    "agentId": "Your Access Key",
    "token": "Your Token",
    "event": {
        "name": "AddAction",
        "type": "dedicated",
        "data" : {
          "service":"OrderCoffee",
          "parameters":{
            map<key, *slu.Value>
          }
        }
    },
    "params": {
        // 事件条件
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
        "name": "DeviceHumanFaceEvent",
        "type": "general"
    },
    "params": {
      "isChild": true
    }
}
```

**event Object**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | true |
| type | string | 可枚举值，可选值有：<br>- dedicated: 有Skill响应的事件 <br>- general: 通用事件，例如Touch, HumanFace | true |
| data | object | 当type==dedicated时，才会有这个字段，描述如下。data用来描述需要由哪个skill来接收此事件，以及相关的槽位信息 | false |

**data Object**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| service | string | skill name | true |
| parameters | map | k: 槽位名(string)，v: 槽位值([slu.Value][03272349]) | false |

  [03272349]: https://github.com/roobo/docs/blob/master/Bot/3-ApiReference/rosai-skills-development-protocol.md#system-object "slu.Value"

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

| 事件名称 | 事件含义 | 参数 | 举例 | deprecated |
| --- | --- | --- | --- | --- |
| ROSAI.TimeoutIntent | 用户输入超时 | "params": {<br>&nbsp;&nbsp;"repeat": int //重复次数，从0开始，1代表第1次重复<br>} | "params": {<br>&nbsp;&nbsp;"repeat": 1<br>} | false |
| ROSAI.handleChangeContextEvent | 变更上文事件(context&slots) | map<k, v> | "params":<br>{<br>&nbsp;&nbsp;"artist":["周杰伦"],<br>&nbsp;&nbsp;"name":["龙卷风"]<br>} | false |
| PowerOnEvent | 开机 | | | true |
| AutomaticNextEvent | 自动下一首 | | | true |
| IdleEvent | 设备空闲 | | | true |
| TouchEvent | 触摸 | //part | //Head //Ear | true |
