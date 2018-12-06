<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Intent Request](#intent-request)
	- [Request format](#request-format)
		- [HTTP Header](#http-header)
		- [Intent Request Body Syntax:](#intent-request-body-syntax)
		- [Intent Request Body Parameters](#intent-request-body-parameters)
		- [Context Object](#context-object)
		- [System Object](#system-object)
- [Intent Response](#intent-response)
	- [Response Body Syntax:](#response-body-syntax)
		- [Results Array](#results-array)
		- [Result Object](#result-object)

<!-- /TOC -->

# Intent Request

## Request format

### HTTP Header

```
POST / HTTP/1.1
Content-Type : application/json;charset=UTF-8
Host : your.application.endpoint
Content-Length :
Accept : application/json
Accept-Charset : utf-8
```

###  Intent Request Body Syntax:

```json
{
  "version": "2.0",
  "context": {
    "system": {
      "skill": {
        "skillId": "rosai1.ask.skill.weather.v1.0"
      },
      "user": {
        "userId": "rosai1.ask.account.001",
        "appId": "rosai1.ask.skill.developer.001"
      },
      "device": {
        "deviceId": "rosai1.device.001"
      }
    }
  },
  "request": {
    "type": "IntentRequest",
    "requestId": "12345",
    "timestamp": "2018-06-21T15:30:02+08:00",
    "intent": {
      "name": "WeatherForADay",
      "confirmationStatus": "NONE",
      "slots": {
        "date": {
          "name": "date",
          "value": {
            "normType": "String",
            "norm": "2018-06-21"
          },
          "confirmationStatus": "NONE"
        },
        "focus": {
          "name": "focus",
          "value": {
            "normType": "String",
            "norm": "天气"
          },
          "confirmationStatus": "NONE"
        }
      }
    }
  }
}
```

###  Intent Request Body Parameters

| Parameter | Description                                                  | type   | required |
| --------- | ------------------------------------------------------------ | ------ | -------- |
| version   | 请求的协议版本标识, 该协议版本是 "2.0"                              | string | true     |
| context   | 为你的技能提供请求关联的设备信息和与rosai交互的当前状态及上下文信息 | object | true     |
| request   | 用户请求的详细信息                                           | object | true     |

### Context Object

| Parameter    | Description                               | type                    | required |
| ------------ | ----------------------------------------- | ----------------------- | -------- |
| system       | 提供当前rosai和设备与该技能交互的状态信息 | object                  | true     |
| context      | 当前技能与多轮相关的上下文信息            | string                  | false    |
| lifespanInMs | 上下文有效时间                            | int64                   | false    |
| parameters   | 与该技能相关的参数信息                    | map<string, *slu.Value> | false    |

### System Object

### slu.Value

| Parameter    | Description     | type      | required |
| ------------ | --------------- | --------- | -------- |
| orgin       | value 的synonym，原值 | object | false     |
| normType    | 值类型    | string，可枚举值，包括：<br> Int, Bool, Float, String, StrArray   | true    |
| norm        | 归一化后的值    | 由normType指定   | true    |

# Intent Response

## Response Body Syntax:

```json
{
  "version": "2.0",
  "status": {
    "code": 0
  },
  "context": {
    "parameters": {
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
              "url": "http://xx.h5"
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

### Results Array

Results 中每一个元素是一个Result object

### Result Object

| Parameter    | Description  | type    | required |
| ------------ | ----------------- | ---------------- | -------- |
| hint    | 语音回复，后续语音输出建议使用outputSpeech | string   | false |
| outputSpeech | 建议VUI回复 | object  | false |
| outputScript | 建议GUI+VUI回复 | object  | false |
| emotions | []emotion object，情感识别结果 | object   | false |
| data | 基础数据 | object  | false  |

### emotion Object

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

### outputSpeech Object

包含这一次response需要VUI输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | type支持"PlainText", "Audio", "EnabledEvent" |  string | true
source | 上面相应type相关数据 | object | true

#### [type = PlainText / Audio]

type | required
--|--
string | true

#### [type = EnabledEvent]

Parameter  | Description  |  type | required
--|--|--|--
name  | 事件名称  |  string | true


### outputScript Object

包含这一次response需要GUI+VUI输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | type支持"Script.H5" |  string | true
source | 上面相应type相关数据 | object | true

#### [type = Script.H5]

Parameter  | Description  |  type | required
--|--|--|--
url  | H5地址  |  string | true
