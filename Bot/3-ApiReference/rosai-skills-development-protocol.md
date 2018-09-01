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
              "ssml": "<speak>北京今天多云，气温23度到35度，东南风2级<audio>https://ai.roobo.com/weather/wind_2.mp3</audio></speak>",
              "displayText": "多云，气温23度到35度，东南风2级"
            }
          },
          {
            "card": {
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
items | 有屏设备的显示信息，一般包含简单输出和card，一般不要超过2个元素。<br>- simpleResponse: 包含展示的文字(**textToDisplay**)和需要说出的ssml(**ssml**)或tts(**textToSpeech**). ssml和textToSpeech不能同时出现。 <br>- card: type支持“Txt“, “Standard“, "Images"(待续...) |  Object Array | false
suggestions | Suggestion片段, 最多8片, 每片最长25个char, 仅支持文本 | Object Array | false

Notes<br>
- 一个response回复里建议最多包含两个simpleResponse对象和最多一个card对象。
- items 数组里的元素在端上是有顺序的。即端上收到解析outputDisplay后，先执行第一个元素的内容，接下来再执行第二个元素的内容。
- items 数组里的每一个元素是simpleResponse和card对象的组合，它们是无顺序的。对于如下一个元素在播放音乐的同时显示标准图片卡片。
```
  {
    "simpleResponse": {
      "audio": "https://ai.roobo.com/song/东风破.wav"
    },
    "card": {
      "type": "Standard",
      "title": "东风破",
      "content": "《东风破》是中国台湾流行音乐男歌手周杰伦演唱的一首歌曲，由周杰伦谱曲，方文山填词，收录在周杰伦2003年7月31日发行的个人第四张国语专辑《叶惠美》中。",
      "image": {
        "url": "https://ai.roobo.com/image/东风破.jpg",
        "altText": "music 东风破"
      }
    }
  }
```

### simpleResponse Object

Parameter  | Description  |  type | required
--|--|--|--
textToSpeech  | 用来发声的普通文本，用来转换成tts，不能和ssml字段同时存在 |  string | false
ssml  |  ssml格式的内容，不能和textToSpeech字段同时存在，例： `<speak>北京今天多云，东南风2级<audio>https://ai.roobo.com/weather/wind_2.mp3</audio></speak>` |  string | false
textToDisplay  | 用来展示的文本  | string  | true
audio  | 音频资源，存放一个音频url，例：https://ai.roobo.com/weather/wind_2.mp3  |  string | false

<hr>

### 文本卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Txt"  |  string | true
title  | 卡片标题 |  string | true
content  | 卡片内容  | string  | true

simple card example:
```
"card": {
  "type": "Txt",
  "title": "北京天气",
  "content": "多云，气温23度到35度，东南风2级"
}
```

### 标准卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Standard"  |  string | true
title  | 卡片标题 |  string | true
content  | 卡片内容  | string  | true
image  | 卡片图片对象  | object |  true

#### Standard card image Object

Parameter  | Description  |  type | required
--|--|--|--
imageUrl  | 图片url, 建议图片的宽度与高度的比是16:9 |  string | true
bulletComment  | 图片弹幕，可以是文字或者表情(\good)，显示在图片上 |  string | false
altText  | 图片获取失败时显示的文本 | string  | true

```
"card": {
  "type": "Standard",
  "title": "东风破",
  "content": "《东风破》是中国台湾流行音乐男歌手周杰伦演唱的一首歌曲，由周杰伦谱曲，方文山填词，收录在周杰伦2003年7月31日发行的个人第四张国语专辑《叶惠美》中。",
  "image": {
    "url": "https://ai.roobo.com/image/东风破.jpg",
    "bulletComment": "\FiveStars",
    "altText": "music 东风破"
  }
```

### 图片卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Images"  |  string | true
list  | 图片对象数组  | image array object |  true

images card example:
```
"card": {
  "type": "Image",
  "list": [
    {
      "url": "https://ai.roobo.com/image/东风破.jpg",
      "bulletComment": "\FiveStars",
      "altText": "music 东风破"
    }，
    {
      "url": "https://ai.roobo.com/image/小夜曲.jpg",
      "altText": "music 小夜曲"
    }
  ]
}
```

### Suggestions Object

引导用户进行下一轮对话的提示样例。
