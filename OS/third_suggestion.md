### /third/suggestion

* [概述](#1-概述)
* [URLs](#2-URLs)
* [请求参数](#3-请求参数)
* [回复参数](#4-回复参数)
* [实例](#5-实例)

### 1 概述

---

引导建议。

### 2 URLs

---

| Method | Definition |
| :--- | :--- |
| POST /third/suggestion | 接收返回均使用JSON表示 |


### 3 请求参数

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| agentId | String | 应用唯一凭证 | Required |
| token | String | 访问凭证 | Required |
| sessionId | String | 会话id | Required |
| chances | []Chance | 时机数组 | Required |

### 4 回复参数

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| status | Status | 状态码 | Required |
| semantic | []Semantic | 引导语义 | Required |
| result | []Result | 引导过程 | Required |

### 5 实例

---

_Sample Request_

```
POST http://ip:port/third/suggestion

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
    "service": "guide2__music",
    "action": "Play",
    "outputContext": {
	  "service": "guide2__music",
	  "context": "yes_or_no",
	  "parameters": { # 结构自定义
		"id":"73323sxe3"
      }
	}
  },
  "result": {
    "hint": "周杰伦发布了新歌《告白气球》，要不要听听？",
    "data": {
      "type": "RUN_ONCE"
    }
  }
}
```

    

```
说明：   
     1. 引导场景名规范：`guide2__$变量`，`guide2__`为固定前缀。
     2. type是一个枚举类型，有两个取值，分别是RUN_ONCE（一次运行），RUN_INCTX（上下文）。
```

