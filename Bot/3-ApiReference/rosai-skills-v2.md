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
		- [outputSpeech Object](#outputspeech-object)
		- [outputDisplay Object](#outputdisplay-object)

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
            "orgin": null,
            "normType": "String",
            "norm": "2018-06-21"
          },
          "confirmationStatus": "NONE"
        },
        "focus": {
          "name": "focus",
          "value": {
            "orgin": null,
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
| version   | 请求的协议版本标识, e.g.: "2.0"                              | string | true     |
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

# Intent Response
===

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
      "hint": "北京今天多云，气温23度到35度，东南风2级",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "北京今天多云，气温23度到35度，东南风2级"
          },
          {
            "type": "SSML",
            "source": "<speak>北京今天<emphasis level=\"strong\">多云</emphasis>，气温23度到35度，东南风2级</speak>"
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
      "outputDisplay": {
        "items": [
          {
            "simpleResponse": {
              "speechText": "北京今天多云，气温23度到35度，东南风2级",
              "displayText": "多云，气温23度到35度，东南风2级"
            }
          },
          {
            "basicCard": {
              "type": "Standard",
              "title": "北京天气",
              "content": "多云，气温23度到35度，东南风2级",
              "image": {
                "url": "www.roobo.com/aicloud/skills/weather/cloudy.jpg",
                "altText": "Image alternate text"
              }
            }
          }
        ],
        "suggestions": [
          {
            "title": "明天"
          },
          {
            "title": "后天"
          }
        ]
      },
      "data": {
        "city": "北京",
        "date": "2018-06-21",
        "weather": "多云",
        "quality": "轻度污染",
        "temperature": "33"
      }
    }
  ]
}
```

### Results Array

Results 中每一个元素是一个Result Object

### Result Object

| Parameter    | Description  | type    | required |
| ------------ | ----------------- | ---------------- | -------- |
| hint         | legacy field, deprecated    | string   | true |
| formatType   | legacy field, deprecated, value: text/audio | string | false  |
| outputSpeech | 针对无屏设备的语音展示 | Object  | false |
| outputDisplay | 针对有屏设备的展示 | Object | false |

### outputSpeech Object

包含这一次response需要语音输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | 表示output speech的type, 有效的type: "PlainText"，"SSML" |  string | true
source | output speech 的内容，根据type来解析<br>- PlainText: 输出tts;<br>- SSML: 符合ssml语法的声音输出方案 | string | true

### outputDisplay Object

Parameter  | Description  |  type | required
--|--|--|--
items | 有屏设备的显示信息，一般包含简单输出和复杂展示，建议不要超过2个元素。<br>- 简单输出: 包含展示的文字和需要说出的tts <br>- 复杂输出: 包括如basicCard, listSelect, carouselSelect, carouselBrowse, tableCard, mediaResponse |  Object Array | false
suggestions | Suggestion片段, 最多8片, 每片最长25个char, 仅支持文本 | Object Array | false
