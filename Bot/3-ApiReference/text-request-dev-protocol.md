## IntentRequest 开发协议

版本：1.0.3

### 大纲

* [简介](#1-简介)
* [Request](#2-Intent-Request)
  * [HTTP Header](#21-http-header)
  * [Request Body Syntax](#22-Request-Body-Syntax)
  * [Context Object](#23-Context-Object)
  * [Location Object](#24-Location-Object)
    * [Address Object](#241-Address-Object)
  * [Lang Object](#25-Lang-Object)
* [Response](#3-Intent-Response)
  * [Response Body Syntax](#31-Response-Body-Syntax)
  * [Semantic Object](#32-Semantic-Object)
  * [Results Object](#33-Results-Array)
    * [Result Object](#331-Result-Object)
      * [Emotion Object](#3311-Emotion-Object)
      * [outputSpeech Object](#3312-outputSpeech-Object)
      * [outputScript Object](#3313-outputScript-Object)

### 1. 简介

本文是对在[_Roobo开放平台_](https://ros.ai)上技能请求协议的详细描述。

### 2. Intent Request

### 2.1 HTTP Header

```
POST / HTTP/1.1
Content-Type : application/json;charset=UTF-8
Host : your.application.endpoint
Content-Length :
Accept : application/json
Accept-Charset : utf-8
```

#### 2.2 Request Body Syntax

_Request_ 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| agentId | String | Access Key | Required |
| token | String | Token | Required |
| sessionId | String | 会话id，如果有clientIId，一般同clientId即可 | Required |
| query | String | 输入query | Required |
| clientId | String | 设备id | Optional |
| lang | Lang Object | [Lang](#24-Lang-Object) | Optional |
| contexts | []Context Object | [Lang](#22-Context-Object) | Optional |
| location | Location Object | [Lang](#23-Location-Object) | Optional |

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

#### 2.3 Context Object

_Context_ 向所请求的CloudApp提供了当前的设备信息，用户信息和应用状态，用以帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| service | String | 服务名 | Required |
| context | String | 上文名称 | Optional |
| parameters  | Map | [Param定义](/Bot/3-ApiReference/rosai-skills-development-protocol.md) | Optional |

#### 2.4 Location Object

__Location__ 向所请求的CloudApp提供了当前的设备的地理信息，用于帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。期望key 统一为 location

| Name | Type | Description | Required |
|--|--|--|--|
|address|object| [address](#231-address定义)| Optional |
|longitude|float|经度| Required |
|latitude|float|纬度| Required |

##### 2.4.1 Address Object

| Name | Type | Description | Required |
|--|--|--|--|
|country|String| 国家| Optional |
|province|String| 所在地区的省份 | Optional |
|city|String|所在的城市| Optional |
|detail|String|详细的地址信息| Optional |

#### 2.5 Lang Object

__Lang__ 向所请求的CloudApp标明应用所选择的_NLP_类型。目前只支持两类中文（__zh__），英文（__en__）。

### 3. Intent Response

根据之前的描述，Response是 _CloudApp_ 返回给CloudAppClient的结果。

#### 3.1 Response Body Syntax

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| reqId | String | 请求的唯一ID | Required |
| status | Status Object | [Status](status.md) | Required |
| query | String | 纠错后的text query | Required |
| semantic | Semantic Object | 语义部分 | Optional |
| results | Results Object | [Results](#33-Results-Array) | Optional |

```
{
  "reqId": "68.1531449273875.a3699090-b716-4bcd-a66e-83c68fdd6672",
  "status": {
    "code": 0,
    "errorType": "success"
  },
  "query": "北京今天天气",
  "semantic": {
    "service": "Weather",
    "action": "WeatherForADay",
    "params": {
      "city": {
        "orgin": null,
        "normType": "String",
        "norm": "北京"
      },
      "date": {
        "orgin": null,
        "normType": "String",
        "norm": "2018-06-21"
      }
    },
    "outputContext": {
      "service": "RMUSIC_1206",
      "context": "media,ack"
    }
  },
  "results": [
    {
      "outputSpeech": {
        "items": [
          {
            "type": "EnabledEvent",
            "source": {
              "name": "@sys.event.TimeoutEvent"
            }
          },
          {
            "type": "PlainText",
            "source": "北京今天晴，气温23度到35度，东南风2级"
          },
          {
            "type": "Audio",
            "source": "https://ai.roobo.com/weather/wind_2.mp3"
          },
          {
            "type": "PlainText",
            "source": "您还可以跟我说 北京空气质量?"
          }
        ]
      },
      "outputScript": {
        "items": [
          {
            "type": "Script.H5",
            "source": {
              "url": "http://weather-template.h5"
            }
          }
        ]
      },
      "data": {
        "city": "北京",
        "date": "2018-06-21",
        "weather": "晴",
        "quality": "轻度污染",
    		"temperature": "33"
      },
      "emotions": [
          {
              "type": "answer",
              "level": 0,
              "code": "A001"
          }
      ]
    }
  ]
}
```

#### 3.2 Semantic Object

_Text query_的语义理解（_NLP_）的结果。

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| service | String | 技能标识 | Required |
| action | String | 意图标识 | Required |
| params | Map | [Map<string, slu.Value>](rosai-skills-development-protocol.md) | Required |
| inputContext | Context 对象 | 输入上文 | Optional |
| outputContext | Context 对象 | 输出下文 | Optional |

#### 3.3 Results Array

Results 中每一个元素是一个Result object

##### 3.3.1 Result Object

| Parameter    | Description  | type    | required |
| ------------ | ----------------- | ---------------- | -------- |
| hint    | 语音回复，后续语音输出建议使用outputSpeech | string   | false |
| outputSpeech | 建议VUI回复 | object  | false |
| outputScript | 建议GUI+VUI回复 | object  | false |
| emotions | []emotion object，情感识别结果 | object   | false |
| data | 基础数据 | object  | false  |

###### 3.3.1.1 Emotion Object

Parameter  | Description  |  type | required
--|--|--|--
type  | 情感识别对象，枚举类型["answer"-语音回复的情绪]  |  string | true
level  | [情感值定义-一级情绪](emotion.md) |  int | true
code  | [情感值定义-二级情绪](emotion.md) |  string | true

simple card example:
```
{
  "type": "answer",
  "level": "1",
  "code": "B001"
}
```

###### 3.3.1.2 outputSpeech Object

包含这一次response需要VUI输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | type支持"PlainText", "Audio", "EnabledEvent" |  string | true
source | 上面相应type相关数据 | object | true

####### [type = PlainText / Audio]

type | required
--|--
string | true

####### [type = EnabledEvent]

Parameter  | Description  |  type | required
--|--|--|--
name  | 事件名称  |  string | true


###### 3.3.1.3 outputScript Object

包含这一次response需要GUI+VUI输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | type支持"Script.H5" |  string | true
source | 上面相应type相关数据 | object | true

####### [type = Script.H5]

Parameter  | Description  |  type | required
--|--|--|--
url  | H5地址  |  string | true
