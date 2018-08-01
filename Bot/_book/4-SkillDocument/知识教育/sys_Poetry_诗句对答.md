# 1. 服务简介（待编辑）

为用户提供诗词对答服务。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| verse | 诗句 | 白日依山尽 |

# 3.意图

**\*\*\*诗句对答返回字段格式规整，在此进行统一说明**

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 对应的诗句 | string |
| data | author | 该诗词的作者 | string |
|  | title | 该诗词的题目 | string |
|  | verse | 对应的诗句 | string |

\/GetLastPhrase
诗句对答意图，机器人会返回用户所说的诗词的上一句，如果已经是第一句，会告知用于已经是第一句。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;verse&gt; | 黄河入海流的上一句是什么 |

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

\/GetNextPhrase

诗句对答意图，机器人会返回用户所说的诗词的下一句，如果已经是最后一句，会告知用户。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;verse&gt; | 白日依山尽的下一句是什么 |

返回样例

```
    "result": {
        "hint": "黄河入海流",
        "data": {
            "author": "王之涣",
            "title": "登鹳雀楼",
            "verse": "黄河入海流"
        }
    }
```

\/GetPhrase
机器人会返回用户所说的下一句，如果用户说的包含多句，则反追最后一句的下一句。如果已经是最后一句，会告知用户。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;verse&gt; | 白日依山尽黄河入海流 |

返回样例

```
    "result": {
        "hint": "欲穷千里目",
        "data": {
            "author": "王之涣",
            "title": "登鹳雀楼",
            "verse": "欲穷千里目"
        }
    }
```

