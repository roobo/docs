### \/bot\/v3\/query

* [概述](#1-概述)
* [URLs](#2-URLs)
* [请求参数](#3-请求参数)
* [回复参数](#4-回复参数)
* [实例](#5-实例)

### 1 概述

---

对输入的自然语言文本进行意图识别。

### 2 URLs

---

| Method | Definition |
| --- | --- |
| POST \/bot\/v3\/query | 接收返回均使用JSON表示 |

### 3 请求参数

---

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| agentId | String | 应用唯一凭证 | Required |
| token | String | 访问凭证 | Required |
| sessionId | String | 会话id | Required |
| query | String | 输入query | Required |
| clientId | String | 设备id | Optional |
| lang | [Lang](/ApiReference/query/lang.md) | 语种，默认中文 | Optional |
| contexts | \[\][Context](/ApiReference/query/context.md) | 上文 | Optional |
| location | [Location](/ApiReference/query/location.md) | 地理位置 | Optional |
| callback | [Callback](/ApiReference/query/callback.md) | 回调参数 | Optional |

### 4 回复参数

---

| Name | Type | Description | Required |
| --- | --- | --- | --- |
| status | Status | 状态码 | Required |
| query | String | 输出query（纠错后） | Required |
| semantic | Semantic | 语义部分 | Optional |
| results | \[\][Result](/ApiReference/query/result.md) | 数据部分 | Optional |

### 5 实例

---

_Sample Request_
双语教学

```
POST http://api.ros.ai/bot/v3/query

Headers:
Content-Type: application/json; charset=utf-8

{
  "agentId":"2ZmNzYyOTA5MzJjZ",
  "token":"f7caaf310da3dcb24bacdc7944456210",
  "sessionId":"1234567890",
  "query":"我要学英语"
}
```

_Sample Response_

```
{
  "status": {
    "code": 0,
    "errorType": "success"
  },
  "query": "我要学英语",
  "semantic": {
    "service": "Elearn",
    "action": "Play",
    "outputContext": {
      "service": "Elearn",
      "context": "Elearn"
    }
  },
  "results": [
    {
      "hint": "双语教学 第一课 来啦!",
      "data": {
        "content": "双语教学 第一课 来啦!",
        "led": "ACTION_CHAT",
        "resId": "e-learn:6",
        "type": "tts"
      },
      "formatType": "text",
      "formatSpeak": "${content}"
    },
    {
      "hint": "我们的朵朵糖飞船即将抵达美丽的南极洲，在冰天雪地的南极洲有一个庞大的水果超市，让我们一起去看看吧。",
      "data": {
        "content": "我们的朵朵糖飞船即将抵达美丽的南极洲，在冰天雪地的南极洲有一个庞大的水果超市，让我们一起去看看吧。",
        "led": "ACTION_CHAT",
        "resId": "e-learn:6",
        "type": "tts"
      },
      "formatType": "text",
      "formatSpeak": "${content}"
    },
    {
      "hint": "",
      "data": {
        "album": "",
        "artist": "",
        "audio": "http://dwn.roo.bo//resource/20170224/3838e0642a6502dc74d765fe2cb0b972.mp3",
        "image": "",
        "led": "ACTION_CHAT",
        "name": "",
        "resId": "e-learn:6",
        "type": "url"
      },
      "formatType": "audio"
    },
    {
      "hint": "瞧！那不是大白熊波比吗，走，咱们过去打个招呼吧,可以说对大白熊波比说 Hi",
      "data": {
        "content": "瞧！那不是大白熊波比吗，走，咱们过去打个招呼吧,可以说对大白熊波比说 Hi",
        "led": "ACTION_CHAT",
        "resId": "e-learn:6",
        "timeout": 7,
        "type": "tts"
      },
      "formatType": "text",
      "formatSpeak": "${content}",
      "timeout": {
        "timeInMs": 7000,
        "action": "timeout?key=349079f0503df3206daf828354f646ae"
      }
    }
  ]
}
```

