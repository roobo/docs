# 事件请求开发协议

版本：2.0.0

## 大纲

* [简介](#1-简介)
* [Event Request](#2-Event-Request)
  * [HTTP-Header](#21-HTTP-Header)
  * [Request Body Syntax](#22-Request-Body-Syntax)
    * [Event Object](#221-Event-Object)
* [Event 命名规范](#23-Event-命名规范)

## 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上事件请求开发协议的详细描述。在当有某种事件发生时产生的，将事件转发给云端的AI策略引擎进行计算。

## 2. Event Request

### 2.1 HTTP Header

```
POST / HTTP/1.1
Content-Type : application/json;charset=UTF-8
Host : your.application.endpoint
Content-Length :
Accept : application/json
Accept-Charset : utf-8
```

### 2.2 Request Body Syntax

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
            "service": "OrderCoffee",
            "context": "coffee",
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
            "params": {
                // 事件参数
            }
        }
    ],
}
```

#### 2.2.1 Event Object

__Event__ 向所请求的CloudApp提供了当前的发生的事件信息，包含事件名和事件参数

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| name | string | 事件名 | true |
| params | Map | 事件参数 | true |

## 3 Event 命名规范

### 系统事件

系统事件名称规则：@sys.event.event_name

| 分段 | 含义 |
| --- | --- |
| @sys.evnet. | 系统事件前缀 |
| event_name  | 事件名，命名规范同C语言变量 |

开放系统事件列表

| 事件名称 | 事件含义 | 参数 |
| --- | --- | --- |
| sys.event.device_power_on  | 开机 | {} |

### 自定义事件

自定义事件名称规则：@event.event_name

| 分段 | 含义 |
| --- | --- |
| @evnet. | 自定义事件前缀 |
| event_name  | 事件名，命名规范同C语言变量 |
