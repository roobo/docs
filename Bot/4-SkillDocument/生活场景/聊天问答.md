## Chat

* [服务说明](#1-服务说明)
* [请求参数](#2-意图说明)
* [实例](#3-实例)
* [emotion](#4-情感分析)
* [source](#5-问答来源)

### 1 服务说明

---
自定义问答、闲聊

### 2 意图说明

---
Chat服务语义部分如下，不区分意图。
```
"semantic": {
	"service": "Chat"
}
```

### 3 实例

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
  "query":"早上好"
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
    "semantic": {
        "service": "Chat",
        "action": "default",
        "outputContext": {
            "service": "Chat",
            "context": "chat"
        }
    },
    "results": [
        {
            "hint": "你好啊，是想请我吃饭吗",
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
                ],
                "source": "chat_roobo"
            }
        }
    ]
}
```
_Chat Result->data_

| 字段名 | Definition | type | 是否是必填字段 |
| :--- | :--- | :--- |:--- |
| hint | 闲聊回复 | string | 必填 |
| emotion | 情感分析结果，分别对问题（question）和答案（answer）做出了情感倾向识别 | string | 已废弃 |
| source | 问答来源 | string | 必填 |

具体枚举值参考如下。

### 4 问答来源
| source | Definition |
| :--- | :--- |
| chat_roobo | Roobo问答 |
| chat_tuling | 图灵问答 |
| chat_xiaohuangji | 小黄鸡问答 |
| qa_sys | 系统自定义问答 |
| qa_usr | 用户自定义问答 |
| qa_dup | 重复自定义问答 |
| qa_unknown | 默认自定义问答 |
| qa_welcome | 欢迎语自定义问答 |

