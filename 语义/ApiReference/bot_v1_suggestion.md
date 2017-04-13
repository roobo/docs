### /bot/v1/suggestion

* [概述](#Overview)
* [URLs](#URLs)
* [请求参数](#aa)
* [回复参数](#dd)
* [POST /bot/v1/suggestion](#bb)

### <span id="Overview">概述</span>

---

引导建议。

### <span id="URLs">URLs</span>

---

| Method | Definition |
| :--- | :--- |
| POST /bot/v1/suggestion | 接收返回均使用JSON表示 |


### <span id="aa">请求参数</span>

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| agentId | String | 应用唯一凭证 | Required |
| token | String | 访问凭证 | Required |
| sessionId | String | 会话id | Required |
| chances | []Chance | 时机数组 | Required |

### <span id="dd">回复参数</span>

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| status | Status | 状态码 | Required |
| semantic | []Semantic | 引导语义 | Required |
| result | []Result | 引导过程 | Required |

### <span id="bb">/bot/v1/suggestion</span>

---

_Sample Request_

```
POST https://api.ros.ai/bot/v1/suggestion

Headers:
Content-Type: application/json; charset=utf-8

{
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "sessionId":"1234567890",
    "chances": [
        {
            "name": "awake_and_notalk_in_5s" # 时机名称
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
  "semantic": {
    "service": "guide__to__music",
    "action": "Play",
    "outputContext": {
	  "service": "guide__to__music",
	  "context": "yes_or_no",
	  "parameters": { # 结构自定义
		"id":"73323sxe3"
      }
	}
  },
  "result": {
    "hint": "周杰伦发布了新歌《告白气球》，要不要听听？",
    "data": {
      "type": "RUN_ONCE" # RUN_INCTX
    }
  }
}
```

