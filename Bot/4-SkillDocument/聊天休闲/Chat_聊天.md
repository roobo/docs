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
| emotion | 情感分析结果，分别对问题（question）和答案（answer）做出了情感倾向识别 | string | 可选 |
| source | 问答来源 | string | 必填 |

具体枚举值参考如下。

### 4 情感分析
*情感分类体系*
当前的情感分类体系参考了业界比较主流的做法，具体可以参考下面两个单位的工作：

 - 国外：Ekman情感分类体系
 - 国内：大连理工大学中文情感词汇本体说明文档
 
| 一级类别 | 二级类别 | 是否支持 | 示例 |
| :--- | :--- | :--- | :--- |
| 正常(normal) | 正常(normal) | Y | - |
| 喜/乐（happy） | 快乐(PA) | Y | 喜悦、欢喜、笑眯眯、欢天喜地 |
| - | 安心(PE) | N | 踏实、宽心、定心丸、问心无愧 |
| 怒（angry） | 愤怒(NA) | N | 气愤、恼火、大发雷霆、七窍生烟 |
| 哀（sad） | 悲伤(NB) | Y | 忧伤、悲苦、心如刀割、悲痛欲绝 |
| - | 失望(NJ) | Y | 憾事、绝望、灰心丧气、心灰意冷 |
| - | 思念(PF) | N | 思念、相思、牵肠挂肚、朝思暮想 |
| - | 内疚(NH) | N | 内疚、忏悔、过意不去、问心无愧 |
| 惧（fear） | 慌张(NI) | N | 慌张、心慌、不知所措、手忙脚乱 |
| - | 恐惧(NC) | N | 胆怯、害怕、担惊受怕、胆战心惊 |
| - | 害羞(NG) | N | 害羞、害臊、面红耳赤、无地自容 |
| 恶（hate） | 烦闷(NE) | N | 憋闷、烦躁、心烦意乱、自寻烦恼 |
| - | 憎恶(ND) | N | 反感、可耻、恨之入骨、深恶痛绝 |
| - | 贬责(NN) | N | 呆板、虚荣、杂乱无章、心狠手辣 |
| - | 妒忌(NK) | N | 眼红、吃醋、醋坛子、嫉贤妒能 |
| - | 怀疑(NL) | N | 多心、生意、将信将疑、疑神疑鬼 |
| 惊（surprise） | 惊奇(PC) | N | 憋闷、烦躁、心烦意乱、自寻烦恼 |

`目前只支持一级分类`

### 5 问答来源
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

