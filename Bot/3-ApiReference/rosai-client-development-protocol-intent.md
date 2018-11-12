## IntentRequest 开发协议

### Roobo 开放平台

版本：1.0.3

### 大纲

* [简介](#1-简介)
  * [一些概念](#11-一些概念)
* [Request](#2-request)
  * [协议概览](#21-协议概览)
  * [Context定义](#22-context-定义)
  * [Location定义](#23-location-定义)
  * [Lang定义](#24-lang定义)
* [Response](#3-response)
  * [协议概览](#31-协议概览)
  * [Status定义](#32-status定义)
  * [Semantic定义](#33-semantic定义)
  * [Results定义](#34-results定义)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上开发Client的IntentRequest协议的详细描述。

#### 1.1 一些概念

在了解本文所描述协议之前，需要对一下概念作如下说明：

* **CloudApp** - 在[_Roobo开放平台_](https://ros.ai)上接入某种云端服务或小应用。
* **CloudDispatcher** - 用于向 CloudApp 传递请求和分发 CloudApp 返回结果的云端模块。
* **CloudClient** - 用于处理 CloudDispatcher 返回结果的设备端的执行容器。
* **TTS** - **T**ext **T**o **S**peech的缩写，这是机器人的语音表达方式。

### 2. Request

_Request_是由CloudAppClient产生的用于向 CloudDispatcher 获取对应返回结果的请求。目前有两种类型的请求：一种是**IntentRequest**，一种是**EventRequest**。**IntentRequest** 根据语音识别和语义理解（_NLP_）的结果创建的，其中会带有（NLP）的信息。**EventRequest**是在当有某种事件发生时产生的，通过_CloudAppClient_转发给当前的_CloudApp_，比如互动游戏中用户5秒无任何输入会产生一个超时事件，当前的_CloudApp_可以选择处理或者不处理。

#### 2.1 协议概览

_Request_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| agentId | String | Access Key | Required |
| token | String | Token | Required |
| sessionId | String | 会话id，如果有clientIId，一般同clientId即可 | Required |
| query | String | 输入query | Required |
| clientId | String | 设备id | Optional |
| lang | Lang | 语种，默认中文 | Optional |
| contexts | Context 对象 | 上文 | Optional |
| location | Location 对象 | 地理位置 | Optional |
| callback | Callback 对象 | 回调参数,deprecated | Optional |

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
    "query": "一杯拿铁"
}
```

#### 2.2 Context 定义

_Context_ 向所请求的CloudApp提供了当前的设备信息，用户信息和应用状态，用以帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| service | String | 服务名 | Required |
| context | String | 上文名称 | Optional |
| parameters  | Map | [Param定义](Bot/3-ApiReference/rosai-skills-deveopment-protocol) | Optional |

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
|province|String| 所在地区的省份 | Required |
|city|String|所在的城市| Required |
|detail|String|详细的地址信息| Required |


#### 2.4 Lang 定义

__Lang__ 向所请求的CloudApp标明应用所选择的_NLP_类型。目前只支持两类中文（__zh__），英文（__en__）。

#### 2.5 Callback 定义

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| service | String | 服务名 | Required |
| action | String | 动作 | Required |

### 3. Response

根据之前的描述，Response是 _CloudApp_ 返回给CloudAppClient的结果。

#### 3.1 协议概览

_Response_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| reqId | String | 请求的唯一ID | Required |
| status | Status 对象 | [Status](status.md) | Required |
| query | String | 纠错后的Text query | Required |
| semantic | Semantic 对象 | 语义部分 | Optional |
| results | Result 对象 | [Result](rosai-skills-development-protocol.md#results-array) | Optional |
| timeout | Timeout 对象 | 超时参数,deprecated | Optional |

```
{
  "reqId": "68.1531449273875.a3699090-b716-4bcd-a66e-83c68fdd6672",
  "status": {
    "code": 0,
    "errorType": "success"
  },
  "query": "唱首周杰伦的歌",
  "semantic": {
    "service": "Music",
    "action": "Play",
    "params": {
      "artist": {
        "orgin": [
          "周杰伦"
        ],
        "normType": "StrArray",
        "norm": [
          "周杰伦"
        ]
      },
      "category": {
        "orgin": [
          "歌"
        ],
        "normType": "StrArray",
        "norm": [
          "音乐"
        ]
      }
    },
    "outputContext": {
      "service": "RMUSIC_1206",
      "context": "media,ack"
    }
  },
  "results": [
    {
      "hint": "为您播放 周杰伦 枫",
      "data": {
        "album": "十一月的萧邦",
        "artist": "周杰伦",
        "audio": "http://...",
        "extra": null,
        "hqAudio": "",
        "hqImage": "http://...",
        "image": "http://...",
        "length": 275,
        "name": "枫",
        "playMode": "",
        "resId": "music:4042292",
        "sid": "1996138142-1531449288105",
        "size": 4416200,
        "start": 0,
        "type": "MUSIC"
      },
      "formatType": "audio"
    }
  ]
}
```

#### 3.2 semantic定义

_Text query_的语义理解（_NLP_）的结果。

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| service | String | 技能标识 | Required |
| action | String | 意图标识 | Required |
| params | Map | [Map<string, slu.Value>](rosai-skills-development-protocol.md) | Required |
| inputContext | Context 对象 | 输入上文 | Optional |
| outputContext | Context 对象 | 输出下文 | Optional |

#### 3.3 Timeout 定义

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| timeInMs | String | 超时时间（ms） | Required |
| action | String | 动作 | Required |
