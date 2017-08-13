## Cloud App 开发协议
### Roobo 开放平台
版本：V3

### 大纲
* [简介](#1-简介)
	* [一些概念](#11-一些概念)
* [Request](#2-request)
	* [协议概览](#21-协议概览)
	* [Context定义](#22-Context定义)
	* [Location定义](#23-Location定义)
	* [Lang定义](#24-Lang定义)
* [Response](#3-response)
	* [协议概览](#31-协议概览)
	* [Action定义](#32-action定义)

### 1. 简介

本文是对在*[Roobo开放平台][developer_website_link]*上开发CloudApp的协议的详细描述。

[developer_website_link]: https://ros.ai

#### 1.1 一些概念

在了解本文所描述协议之前，需要对一下概念作如下说明：

* **CloudApp** - 在*[Roobo开放平台][developer_website_link]*上接入的云端应用，可以理解为遵循本文所描述的协议开发的某种云端服务或小应用。
* **TTS** - **T**ext **T**o **S**peech的缩写，这是机器人的语音表达方式。

### 2. Request

*Request*是服务端与设备端之间的通讯协议（不包括语音类请求），由设备端产生，并向服务端获取对应返回结果的请求。目前有两种类型的请求：一种是**IntentRequest**，一种是**EventRequest**。**IntentRequest** 是根据语义理解（*NLP*）的结果创建的。**EventRequest**是在当有某种事件发生时产生的，事件分设备端与服务端两类事件，*CloudApp*可以选择处理或者不处理。（事件请求目前处于内测阶段，敬请更新）

#### 2.1 Request 协议预览


*Request* 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| agentId | String | 应用唯一凭证 | Required |
| token | String | 访问凭证 | Required |
| sessionId | String | 会话id | Required |
| query | String | 输入query | Required |
| clientId | String | 设备id | Optional |
| lang | Lang（枚举） | 语种，默认中文 | Optional |
| contexts | Context 对象 | 上文 | Optional |
| location | Location 对象 | 地理位置 | Optional |
| reqId | String | 当前请求的唯一ID | Optional |

```
{
    "agentId": "JmY2Q5MDBiNjI5Mm",
    "token": "943acb75fc4797249b50d085b8c437e9",
    "sessionId": "1472722107",
    "clientId": "sn123456",
    "lang": "chn",
    "contexts": [
        {
            "context": "coffee",
            "service": "OrderCoffee",
            "parameters": {
                "userId": "blm_rlco03m",
                "contactId": "1486539416366"
            }
        }
    ],
    "location": {
        "address": {
            "province": "北京",
            "detail": "北京朝阳区北苑家园121号",
            "city": "北京",
            "country": "中国"
        },
        "longitude": 0,
        "latitude": 0
    },
    "query": "一杯拿铁"
}
```

#### 2.2 Context 定义

*Context* 向所请求的CloudApp提供了当前的设备信息，用户信息和应用状态，用以帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| service | String | 服务名 | Required |
| context | String | 上文名称 | Optional |
| parameters | 自定义对象 | 上文参数 | Optional |

```
    "contexts": [
        {
            "context": "coffee",
            "service": "OrderCoffee",
            "parameters": {
                "userId": "blm_rlco03m",
                "contactId": "1486539416366"
            }
        }
    ]
```

#### 2.3 Location 定义

*Location * 向所请求的CloudApp提供了当前的设备的地理信息，用于帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

```
{
    "latitude": 37.4256293,
    "longitude": -122.20539,
    "address": {
        "country": "中国",        
        "province":"北京"
        "city": "北京",
        "detail": "北京朝阳区北苑家园121号"
    }
}
```

#### 2.4 Lang 定义

*Lang * 向所请求的CloudApp标明应用所选择的*NLP*类型。目前只支持两类中文（*zh*），英文（*en*）。

### 3. Response

根据之前的描述，Response是 *CloudApp* 向客户端的返回结果。

#### 3.1 协议概览

整体协议示例如下：

```

```

