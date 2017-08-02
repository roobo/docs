# 1. 服务简介

为用户提供诗词对答，诗词点播等功能。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| title | 诗词题目 | 静夜思 |
| author | 作者 | 李白 |
| verse | 诗句 | 白日依山尽 |
| type | 诗词类型 | 唐诗 |

# 3.意图

\/GetLastPhrase
诗句对答意图，机器人会返回用户所说的诗词的上一句，如果已经是第一句，会告知用于已经是第一句。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;verse&gt; | 黄河入海流的上一句是什么 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 对应的诗句 | string |
| data | author | 该诗词的作者 | string |
|  | title | 该诗词的题目 | string |
|  | verse | 对应的诗句 | string |

返回样例

```
    "result": {
        "hint": "白日依山尽",
        "data": {
            "author": "王之涣",
            "title": "登鹳雀楼",
            "verse": "白日依山尽"
        }
    }
```

