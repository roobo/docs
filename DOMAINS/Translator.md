## Translator

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [Translate](#1Translate)
 * [Translate](#2Translate)
 * [Translate](#3Translate)
 * [Translate](#4Translate)
 * [Translate](#5Translate)

### 服务说明 {#服务说明}

---

\(**Translator**\)

### 意图说明 {#意图说明}

---

该服务主要有5个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| Translate |  |  | translator |
| Translate |  |  | need_word |
| Translate |  |  | require_word |
| Translate |  | need_word | translator |
| Translate |  | translator | translator |

#### Translate {#1Translate}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| lang | @sys.entity.lang |  |
| word | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"苹果用英语怎么翻译",
    "semantic":{
        "action":"Translate",
        "params":{
            "lang":{
                "code":0,
                "norm":"en",
                "orgin":"英语"
            },
            "word":{
                "code":0,
                "norm":"苹果",
                "orgin":"苹果"
            }
        },
        "service":"Translator"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "destlang":"en",
            "srclang":"ch",
            "resource":{
                "chinese_word":"",
                "tts":"",
                "en_word":"",
                "url":"http://dwn.roo.bo/voices/translate/a/apple.wav"
            }
        },
        "hint":"小主人，请认真听"
    }
}

```

#### Translate {#2Translate}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"苹果用英语怎么翻译",
    "semantic":{
        "action":"Translate",
        "params":{
            "lang":{
                "code":0,
                "norm":"en",
                "orgin":"英语"
            },
            "word":{
                "code":0,
                "norm":"苹果",
                "orgin":"苹果"
            }
        },
        "service":"Translator"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "destlang":"en",
            "srclang":"ch",
            "resource":{
                "chinese_word":"",
                "tts":"",
                "en_word":"",
                "url":"http://dwn.roo.bo/voices/translate/a/apple.wav"
            }
        },
        "hint":"小主人，请认真听"
    }
}

```

#### Translate {#3Translate}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"苹果用英语怎么翻译",
    "semantic":{
        "action":"Translate",
        "params":{
            "lang":{
                "code":0,
                "norm":"en",
                "orgin":"英语"
            },
            "word":{
                "code":0,
                "norm":"苹果",
                "orgin":"苹果"
            }
        },
        "service":"Translator"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "destlang":"en",
            "srclang":"ch",
            "resource":{
                "chinese_word":"",
                "tts":"",
                "en_word":"",
                "url":"http://dwn.roo.bo/voices/translate/a/apple.wav"
            }
        },
        "hint":"小主人，请认真听"
    }
}

```

#### Translate {#4Translate}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| word | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"苹果用英语怎么翻译",
    "semantic":{
        "action":"Translate",
        "params":{
            "lang":{
                "code":0,
                "norm":"en",
                "orgin":"英语"
            },
            "word":{
                "code":0,
                "norm":"苹果",
                "orgin":"苹果"
            }
        },
        "service":"Translator"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "destlang":"en",
            "srclang":"ch",
            "resource":{
                "chinese_word":"",
                "tts":"",
                "en_word":"",
                "url":"http://dwn.roo.bo/voices/translate/a/apple.wav"
            }
        },
        "hint":"小主人，请认真听"
    }
}

```

#### Translate {#5Translate}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| word | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"苹果用英语怎么翻译",
    "semantic":{
        "action":"Translate",
        "params":{
            "lang":{
                "code":0,
                "norm":"en",
                "orgin":"英语"
            },
            "word":{
                "code":0,
                "norm":"苹果",
                "orgin":"苹果"
            }
        },
        "service":"Translator"
    },
    "result":{
        "formatType":"audio",
        "data":{
            "destlang":"en",
            "srclang":"ch",
            "resource":{
                "chinese_word":"",
                "tts":"",
                "en_word":"",
                "url":"http://dwn.roo.bo/voices/translate/a/apple.wav"
            }
        },
        "hint":"小主人，请认真听"
    }
}

```

