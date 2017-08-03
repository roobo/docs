# 1. 服务简介

为用户提供翻译服务，资源来自百度翻译\/有道翻译API，可以提供27种语言的翻译。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| word | 用户需要翻译的词 | 苹果 |
| lang | 语言 | 英语、法语 |

# 3.意图

\*\*\*由于Translate意图、Repeat意图和Change意图返回字段相同，在此统一说明

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | Apple | string |
| data | destlang | 目标语言类 | string |
|  | dstword | 翻译结果 | string |
|  | speed | 语速 | string |
|  | srclang | 源语言 | string |
|  | srcword | 待翻译词汇 | string |
|  | url | 翻译结果音频url | string |
|  | volume | 音量 | string |

\/Translate

包括进入场景，翻译等功能

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 我要翻译 |
|  | 能帮我翻译英文么 |
| &lt; word&gt; + &lt; lang&gt; | 苹果用英语怎么说 |

返回样例

```
    "result": {
        "hint": "Apple",
        "data": {
            "destlang": "en",
            "dstword": "Apple",
            "speed": "",
            "srclang": "zh",
            "srcword": "苹果",
            "url": "http://dwn.roo.bo/voices/translate/a/apple.wav",
            "volume": ""
        }
    }
```

\/Repeat

重复



\/Change

换一种说法，如快乐第一次翻译成happy，换一种说法为 delight

返回样例 



