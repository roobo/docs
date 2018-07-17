## EventRequest 开发协议

### Roobo 开放平台

版本：1.0.1

### 大纲

* [简介](#1-简介)
  * [一些概念](#11-一些概念)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
* [Response](#3-response)
  * [协议概览](#31-协议概览)
  * [Status定义](#32-status定义)
  * [Semantic定义](#33-semantic定义)
  * [Results定义](#34-results定义)
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
| event | Object | 事件对象，包含事件名和事件相关定义 | Required |
| clientId | string | 设备id | Required |
| agentId | string | Access Key | Required |
| token | string | Token | Required |
| params | Object | 事件服务端需要的参数信息 | Required |

```
{
    "event": {
        "name": "ROSAI.AddIntent",
        "nominated": true
    },
    "clientId": "1015000000000093",
    "agentId": "Your Access Key",
    "token": "Your Token",
    "params": {
        "services": [
            "AiLive"
        ],
        "parameters": {
            // 槽位
            map<string, *slu.Value>
        },
        "extra": {
            // 用户自定义
        }
    }
}
```

**event Object**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | Required |
| nominated | bool | 标识是否有指定的skill响应该事件，<br>如果有指定，则需要在params段的services中列出需要响应该事件的skill names | Required |

**params Object**

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| services | string array | 发送方指定的可响应该事件的skill names | Optional |
| parameters | map | k: 槽位名(string)，v: 槽位值([slu.Value][03272349]) | Optional |
| extra | map | 针对该事件，用户自定义参数 | Optional |

  [03272349]: https://github.com/roobo/docs/blob/master/Bot/3-ApiReference/rosai-skills-development-protocol.md#system-object "slu.Value"

### 3. Response

根据之前的描述，Response是 _CloudApp_ 向客户端的返回结果。

#### 3.1 协议概览

_Response_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| status | Status 对象 | [Status](status.md) | Required |
| instructions | Instruction　对象 | 结果，包括指令和其他参数，deprecated | Optional |
| result | Result 对象 | [Result](rosai-skills-development-protocol.md#results-array) | Optional |

```
{
    "status":{
        "code":0,
        "errorType":"success"
    },
    "instructions":[
        {
            "name":"Play",
            "url":"http://..."
        },
        {
            "name":"Play",
            "url":"http://..."
        }
    ]
}
```

### 4. Event

#### 4.1 旧的事件，返回结果Instruction

| 事件名称 | 事件含义 | 参数 | 举例 |
| --- | --- | --- | --- |
| PowerOnEvent | 开机事件 | | |
| AutomaticNextEvent | 自动下一首事件 | | |
| IdleEvent | 设备空闲事件 | | |
| TouchEvent | 触摸事件 | //part | //Head //Ear |

#### 4.2 ROSAI.xxIntent 事件，返回结果Result

| 事件名称 | 事件含义 | 参数 | 举例 |
| --- | --- | --- | --- |
| ROSAI.TimeoutIntent | 用户输入超时事件 | {<br>&emsp;"extra":{<br>&emsp;&emsp;"service":"场景名"<br>&emsp;}<br>} | {<br>&emsp;"extra":{<br>&emsp;&emsp;"service":"AiLivePoetry"<br>&emsp;}<br>} |
