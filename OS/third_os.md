### /third/os

* [概述](#1-概述)
* [URLs](#2-URLs)
* [请求参数](#3-请求参数)
* [回复参数](#4-回复参数)
* [实例](#5-实例)

### 1 概述

---

内部使用接口。对输入的自然语言文本进行意图识别，如果有引导，则结合引导结果一并返回。

### 2 URLs

---

| Method | Definition |
| :--- | :--- |
| POST /third/os | 接收返回均使用JSON表示 |

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
| query | String | 输出query（纠错后） | Optional |
| datas | [] (Semantic,Result) | （***协议变更点***） | Optional |

### 5 实例

---

_Sample Request_

```
POST http://ip:port/third/os

Headers:
Content-Type: application/json; charset=utf-8

{
  "agentId":"2ZmNzYyOTA5MzJjZ",
  "token":"f7caaf310da3dcb24bacdc7944456210",
  "sessionId":"1234567890",
  "query":"你好"
}
```

_Sample Response_

```
{
    "status": {
        "code": 0,
        "errorType": "success"
    },
    "query": "你好",
    "datas": [
        {
            "semantic": {
                "service": "Chat"
            },
            "result": {
                "hint": "你这么关心我，我好感动呀",
                "data": {
                    "emotion": [
                        {
                            "type": "text_question",
                            "value": "normal",
                            "score": ""
                        },
                        {
                            "type": "text_answer",
                            "value": "normal",
                            "score": ""
                        }
                    ]
                }
            }
        },
        {
            "semantic": {
                "service": "guide2__music",
                "action": "Play",
                "outputContext": {
                    "service": "guide2__music",
                    "context": "yes_or_no",
                    "parameters": {
                        "id": "73323sxe3"
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
    ]
}
```




