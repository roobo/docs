### /v1/query

* [Overview](#Overview)
* [URLs](#URLs)
* [Query Parameters and JSON Fields](#query_1)
* [POST /v1/query](#query_2)
* [POST Response](#query_3)

### Overview {#Overview}

---

对输入的自然语言文本进行意图识别，返回意图名称及其参数。

### URLs {#URLs}

---

| Method | Definition |
| :--- | :--- |
| POST /v1/query | 接收返回均使用JSON表示 |

### Query Parameters and JSON Fields {#query_1}

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| query | String | 文本自然语言 \(&lt;=255 char\) | Required |
| sessionId | String | 用于区分client并为其管理上下文信息 \(&lt;=128 char\) | Required |
| agentId | String | 应用唯一凭证 \(&lt;=64 char\) | Required |
| token | String | 访问凭证 \(&lt;=64 char\) | Required |
| contexts | String | Context对象数组，若client输入上文，替换server上文 | Optional |
| location | String | Location对象，可以包含经纬度以及详细地址 | Optional |

### /v1/query {#query_2}

---

_Sample Request_

```
POST http://api.ros.ai/v1/query

Headers:
Content-Type: application/json; charset=utf-8

{
    "query":"唱首周杰伦的东风破",
    "sessionId":"1234567890",
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ"
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

### Response {#query_3}

| Name | Type | Description |
| :--- | :--- | :--- |
| status | [Status](#query_1) Object | 返回成功失败信息 |
| query |  |  |
| semantic |  |  |
| result |  |  |



