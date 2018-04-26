## Cloud App 开发协议
### Roobo 开放平台
版本：V3

API：http://api.ros.ai/bot/v3/query

协议：HTTP POST

### 大纲
* [简介](#1-简介)
    * [一些概念](#11-一些概念)
* [Request](#2-request)
    * [协议概览](#21-协议概览)
    * [Context定义](#22-context定义)
    * [Location定义](#23-location定义)
    * [Lang定义](#24-lang定义)
* [Response](#3-response)
    * [协议概览](#31-协议概览)
    * [Status定义](#32-status定义)
    * [Semantic定义](#33-semantic定义)
    * [Results定义](#34-results定义)

### 1. 简介

本文是对在*[Roobo开放平台][developer_website_link]*上开发CloudApp的协议的详细描述。

[developer_website_link]: https://ros.ai

#### 1.1 一些概念

在了解本文所描述协议之前，需要对一下概念作如下说明：

* **CloudApp** - 在*[Roobo开放平台][developer_website_link]*上接入的云端应用，可以理解为遵循本文所描述的协议开发的某种云端服务或小应用。
* **TTS** - **T**ext **T**o **S**peech的缩写，这是机器人的语音表达方式。

### 2. Request

*Request*是服务端与设备端之间的通讯协议（不包括语音类请求），由设备端产生，并向服务端获取对应返回结果的请求。目前有两种类型的请求：一种是**IntentRequest**，一种是**EventRequest**。**IntentRequest** 是根据语义理解（*NLP*）的结果创建的。**EventRequest**是在当有某种事件发生时产生的，事件分设备端与服务端两类事件，*CloudApp*可以选择处理或者不处理。（事件请求目前处于内测阶段，敬请更新）

#### 2.1 协议概览

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

#### 2.2 Context定义

*Context* 向所请求的CloudApp提供了当前的设备信息，用户信息和应用状态，用以帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| service | String | 服务名 | Required |
| context | String | 上文名称 | Optional |

```
    "contexts": [
        {
            "context": "coffee",
            "service": "OrderCoffee",
        }
    ]
```

#### 2.3 Location定义

*Location * 向所请求的CloudApp提供了当前的设备的地理信息，用于帮助CloudApp更好的去管理逻辑，状态以及对应的返回结果。

```
{
    "latitude": 37.4256293,
    "longitude": -122.20539,
    "address": {
        "country": "中国",        
        "province":"北京",
        "city": "北京",
        "detail": "北京朝阳区北苑家园121号"
    }
}
```

#### 2.4 Lang定义

*Lang * 向所请求的CloudApp标明应用所选择的*NLP*类型。目前只支持两类中文（*zh*），英文（*en*）。

### 3. Response

根据之前的描述，Response是 *CloudApp* 向客户端的返回结果。

#### 3.1 协议概览

*Response* 的整体协议定义如下所示：

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| status | Status 对象 | 状态码 | Required |
| query | String | 纠错后的Text query | Required |
| reqId | String | 当前请求的唯一ID | Required |
| semantic | Semantic 对象 | 语义部分 | Optional |
| results | Result 对象 | 数据部分 | Optional |

```
{
  "status": {
    "code": 0,
    "errorType": "success"
  },
  "query": "唱首歌",
  "reqId": "ZmVjNVlXRmxOR05rTlRnd1pHVTFhOGE1",
  "semantic": {
    "service": "Music",
    "action": "Play",
    "outputContext": {
      "service": "Music",
      "context": "music"
    }
  },
  "results": [
  {
    "hint": "为您播放 傻傻的爱你",
    "data": {
      "album": "单曲 - 傻傻的爱你",
      "artist": "",
      "audio": "http://dwn.roo.bo/resource/music_bk/849/34678849.mp3"
      "hqAudio": "",
      "hqImage": "https://y.gtimg.cn/music/photo_new/T002R300x300M000003ZzeCk0Svi3K.jpg?max_age=2592000",
      "image": "https://y.gtimg.cn/music/photo_new/T002R300x300M000003ZzeCk0Svi3K.jpg?max_age=2592000",
      "name": "傻傻的爱你",
      "resId": "music:5492123",
      "start": 0
    },
    "formatType": "audio"
  }
  ]
}
```
#### 3.2 status定义

返回结果状态标识，*code*是返回码，*errorType*是错误类型，*errorDetails*时候错误详情。

```
{
    "code":400,
    "errorType":"bad_request",
    "errorDetails":"token校验不通过"
}
```

| Status Code | Error Type | Description |
| :--- | :--- | :--- |
| 0 | success | 成功 |
| 1 | no\_result | 无结果 |
| 400 | bad\_request | 不合法的输入 |
| 401 | unauthorized | 权限校验失败 |
| 500 | internal | 系统错误，重试可能有效 |
| 501 | not_supported | 语义 |
| 503 | too_many_requests | 在一定时间内访问次数超限 |
| 601 | service_unreachable | 第三方服务不可用 |
| 602 | service_unknown_format | 第三方服务返回的数据格式有误 |

#### 3.3 semantic定义

*Text query*的语义理解（*NLP*）的结果。

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| service | String | 技能标识 | Required |
| action | String | 意图标识 | Required |
| params | Slot 对象 | 槽位对象，每个技能分别有哪些槽位，请参考技能的具体描述 | Required |
| inputContext | Context 对象 | 输入上文 | Optional |
| outputContext | Context 对象 | 输出下文 | Optional |

```
    "semantic": {
        "service": "Music",
        "action": "Play",
        "params": {
            "artist": {
                "orgin": "[{\"artist\":\"刘德华\"}]",
                "norm": "[{\"artist\":\"刘德华\"}]"
            },
            "name": {
                "orgin": "忘情水",
                "norm": "忘情水"
            }
        },
        "inputContext": {
            "service": "Music",
            "context": "music"
        },
        "outputContext": {
            "service": "Music",
            "context": "music"
        }
    }
```

#### 3.4 results定义

技能的数据部分，results是一个**json数组**。

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| hint | String | **TTS**内容  | Required |
| data | 自定义对象 | 技能自定义 | Optional |
| formatType | String | 标准化同类技能字段输出，便于设备端接。默认可以为空。 | Optional |

---

* **formatType**

_audio_
```
   {
      "hint": "准备播放 Opposites Song",
      "data": {
         "album": "叶惠美",              // 专辑名
         "artist": "周杰伦",                // 艺术家
         "audio": "http://...",              // 播放链接
         "hqAudio": "",                     // 高质量播放链接
         "hqImage": "",                    // 专辑封面链接
         "image": "",                        // 高清专辑封面链接
         "name": "以父之名",          // 歌曲名
         "resId": "aires:114423",     // 资源标识
         "start": 0,                            // 断点
         "extra": null,               //额外信息
         "sid": "0-1513862035533",    //相当于sessionid
         "size": 0,                   //文件大小(B)
         "length": 21,                //播放时长(s)
         "type": "AUDIO"              //资源类型
      },
      "formatType": "audio"
   }
```

_text_
```
   {
      "hint": "今天出门时，碰到隔壁的小孩在他爸爸的车上画东西，就问他在干吗？小孩神秘兮兮地用手遮住，说：“我爸爸揍我了，我要搞破坏！你别告诉他是我在他车上写的。”我点头答应了。回家时，又听到小孩的哭声。我好奇地走近那辆车一看，车门上用小石子写着：“老爸是坏蛋。”",
      "data": {
         "content": "今天出门时，碰到隔壁的小孩在他爸爸的车上画东西，就问他在干吗？小孩神秘兮兮地用手遮住，说：“我爸爸揍我了，我要搞破坏！你别告诉他是我在他车上写的。”我点头答应了。回家时，又听到小孩的哭声。我好奇地走近那辆车一看，车门上用小石子写着：“老爸是坏蛋。"   // 文本内容
      },
      "formatType": "text"
   }
```

* **audio** - 标准字段为**audio**,**hqAudio**,**name**，其中**audio**,**name**为必备字段，其它字段建议命名如上。
* **text** - 标准字段为**content**，**content**为必备字段，其它字段建议命名如上。
