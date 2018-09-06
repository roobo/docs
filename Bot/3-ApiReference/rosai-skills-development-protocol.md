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
		- [display directive Object](#display-directive-object)
		  - [文本卡片](#文本卡片)
		  - [标准卡片](#标准卡片)
            - [图片对象](#图片对象)
            - [弹幕对象](#弹幕对象)
		  - [图片卡片](#图片卡片)
		  - [列表卡片](#列表卡片)
		  - [Suggestions Object](#Suggestions-Object)
		- [event directive object](#event-directive-object)

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
      "directives": [
        {
          "type": "Display.Customized",
          "hint": "多云，气温23度到35度，东南风2级",
          "card": {
            "type": "Standard",
            "title": "北京天气",
            "content": "多云，气温23度到35度，东南风2级",
            "image": {
              "bulletScreen": {
                "imageUrl": "https://ai.roobo.com/image/upvote.jpg",
                "text": "赞"
              },
              "url": "www.roobo.com/aicloud/skills/weather/cloudy.jpg"
            }
          },
          "suggestions": [
            "明天",
            "后天"
          ]
        },
        {
          "type": "ROSAI.EVENT",
          "event": {
            "name": "ROSAI.TimeoutEvent",
            "period": 10000
          }
        }
      ],
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

Results 中每一个元素是一个Result object

### Result Object

| Parameter    | Description  | type    | required |
| ------------ | ----------------- | ---------------- | -------- |
| hint         | tts, legacy field, deprecated | string   | false |
| outputSpeech | 语音输出 | object  | false |
| directives | 针对给定接口的设备级响应的指令数组，如ROSAI.EVENT, Display.Customized | directive object array | false |
| data | bot返回的所有原始数据  | object  | false  |

### outputSpeech Object

包含这一次response需要语音输出的所有资源，其中items是一个 Object Array.

Parameter  | Description  |  type | required
--|--|--|--
type | 表示output speech的type, 有效的type: "PlainText"，"SSML", "Audio" |  string | true
source | output speech 的内容，根据type来解析<br>- PlainText: 输出tts;<br>- SSML: 符合ssml语法的声音输出方案;<br>- Audio: 输出音频文件 | string | true

### display directive object

显示指令(display directive Object)在directives字段里只允许有一个

Parameter  | Description  |  type | required
--|--|--|--
type | 指定该directive的类型 |  string | true
hint | 屏幕上显示的提示文字 | string | false
card  | type支持“Text“, “Standard“, "Images", "List", "Timer" (待续...) | object | false
suggestions | Suggestion片段, 最多8片, 每片最长25个char, 仅支持文本 | string array | false

<br>
**Notes**:<br>
每次交互，云端返回给端上的response，不一定都会带上card。<br>
对于不带card的response，端上不要清除上一次交互返回的response里的card展示，以做到状态保持。<br>
对于端上接收到带card的response，端上替换目前在展示的card展示。

### event directive object

Parameter  | Description  |  type | required
--|--|--|--
type | 指定该directive的类型,固定值为“ROSAI.EVENT” |  string | true
event | event对象，包含事件名(name)和端上处理事件的等待时间(period，单位ms) | [event object](#event object) | true

#### event object

Parameter  | Description  |  type | required
--|--|--|--
name | 事件名,该事件需在事件引擎已注册 |  string | true
period | 端上处理事件的等待时间 | int | true

#### 文本卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Text"  |  string | true
title  | 卡片标题 |  string | true
content  | 卡片内容  | string  | true

simple card example:
```
"card": {
  "type": "Text",
  "title": "北京天气",
  "content": "多云，气温23度到35度，东南风2级"
}
```

#### 标准卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Standard"  |  string | true
title  | 卡片标题 |  string | true
content  | 卡片内容  | string  | true
image  | 图片对象  | [image object](#图片对象) |  true

Standard card example:
```
"card": {
  "type": "Standard",
  "title": "东风破",
  "content": "《东风破》是中国台湾流行音乐男歌手周杰伦演唱的一首歌曲，由周杰伦谱曲，方文山填词，收录在周杰伦2003年7月31日发行的个人第四张国语专辑《叶惠美》中。",
  "image": {
    "url": "https://ai.roobo.com/image/东风破.jpg",
    "bulletScreen": {
      "period": 3000,
      "imageUrl": "https://ai.roobo.com/image/upvote.jpg",
      "text": "十二个赞"
    }
  }
}
```

##### 图片对象

Parameter  | Description  |  type | required
--|--|--|--
url  | 图片url |  string | true
bulletScreen  | 弹幕信息  | [bulletScreen](#弹幕对象) object  |  false

##### 弹幕对象

Parameter  | Description  |  type | required
--|--|--|--
imageUrl  | 弹幕图片url |  string | false
text  | 弹幕文字  | string  |  false
position  |  弹幕位置，支持 “top”, "bottom", "left", "right", "center", "full", "top-left", "top-right", "bottom-left", "bottom-right", 默认是"bottom"（如果是"full"，建议端上做到50%透明度） |  string | false
period  | 弹幕显示时间，单位为ms, 0代表不消失 | int  |  false

#### 图片卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"Images"  |  string | true
list  | 图片对象数组  | [image object](#图片对象) array |  true

images card example:
```
"card": {
  "type": "Images",
  "list": [
    {
      "url": "https://ai.roobo.com/image/东风破.jpg"
    }，
    {
      "url": "https://ai.roobo.com/image/小夜曲.jpg"
    }
  ]
}
```

#### 列表卡片

Parameter  | Description  |  type | required
--|--|--|--
type  | 卡片类型，固定值为"List"  |  string | true
list  | 标准卡片对象数组  | [标准卡片](#标准卡片) array |  true

List card example:
```
"card": {
  "type": "List",
  "list": [
    {
      "type": "Standard",
      "title": "东风破",
      "content": "《东风破》是中国台湾流行音乐男歌手周杰伦演唱的一首歌曲，由周杰伦谱曲，方文山填词，收录在周杰伦2003年7月31日发行的个人第四张国语专辑《叶惠美》中。",
      "image": {
        "url": "https://ai.roobo.com/image/东风破.jpg"
      }
    },
    {
      "type": "Standard",
      "title": "祝福",
      "content": "《祝福》是由丁晓雯作词，郭子作曲，张学友演唱的一首歌曲，收录于1993年12月11日发行的专辑《祝福》中。",
      "image": {
        "url": "https://ai.roobo.com/image/张学友_祝福.jpg"
      }
    }
  ]
}
```

#### Suggestions Object

引导用户进行下一轮对话的提示样例。
