## 2.16 Translator

---

### 2.1.1 服务说明

> \(**Translator**\)

### 2.1.2 意图说明

> 该服务主要有5个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **Translate**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Translate |   |   | translator | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | lang | @sys.entity.lang |   |
>   | word | @sys.any |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
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
        "formatType":"prop",
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
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 2 . **Translate**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Translate |   |   | need_word | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
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
        "formatType":"prop",
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
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 3 . **Translate**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Translate |   |   | require_word | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
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
        "formatType":"prop",
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
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
