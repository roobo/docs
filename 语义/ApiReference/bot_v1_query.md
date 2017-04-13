### /bot/v1/query

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
| :--- | :--- |
| POST /bot/v1/query | 接收返回均使用JSON表示 |

### 3 请求参数

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| agentId | String | 应用唯一凭证 | Required |
| token | String | 访问凭证 | Required |
| sessionId | String | 会话id | Required |
| query | String | 输入query | Required |
| contexts | Context[] | 上文 | Optional |
| location | Location | 地理位置 | Optional |
| callback | Callback | 回调参数 | Optional |

### 4 回复参数

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| status | Status | 状态码 | Required |
| query | String | 输出query（纠错后） | Required |
| semantic | Semantic | 语义部分 | Required |
| results | Result | 数据部分 | Optional |


### 5 实例

---

_Sample Request_

```
POST http://api.ros.ai/bot/v1/query

Headers:
Content-Type: application/json; charset=utf-8

{
  "agentId":"2ZmNzYyOTA5MzJjZ",
  "token":"f7caaf310da3dcb24bacdc7944456210",
  "sessionId":"1234567890",
  "query":"唱首周杰伦的东风破",
  "contexts": [
    {
      "context": "Media",
      "service": "media"
    }
  ]
}
```

_Sample Response_

```
{
  "status": {
    "code": 0,
    "errorType": "success"
  },
  "query": "唱首周杰伦的东风破",
  "semantic": {
    "service": "Media",
    "action": "Play",
    "params": {
      "artist": {
        "orgin": "周杰伦",
        "norm": "周杰伦",
        "code": 0
      },
      "name": {
        "orgin": "东风破",
        "norm": "东风破",
        "code": 0
      }
    }
  },
  "result": {
    "hint": "准备播放",
    "data": {
      "album": "The Era 2010 超时代演唱会",
      "artist": "周杰伦",
      "audio": "http://stream11.qqmusic.qq.com/30846764.mp3",
      "extra": {
        "httpheaders": {
          "Cookie": "pgv_pvid=181; qqmusic_uin=10376; qqmusic_key=1480598554; qqmusic_fromtag=0"
        },
        "style": "流行"
      },
      "image": "http://i.gtimg.cn/music/photo/mid_album_300/L/r/002o2a5G46ETLr.jpg",
      "keywords": null,
      "name": "东风破",
      "resId": "music:2529245",
      "sid": "1788061692-1481073812964",
      "start": 0,
      "trigger": "voice",
      "triggerId": null,
      "type": "MUSIC"
    },
    "formatType": "audio"
  }
}
```
