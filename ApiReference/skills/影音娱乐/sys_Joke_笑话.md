# 1. 服务简介

根据用户点播的标签，播放笑话。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| joke\_tag | 笑话标签 | 冷、校园、儿童 |

# 3.意图

\/GetJoke

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;joke\_tag&gt; | 我要听冷笑话 |
|  | 讲个笑话 |

返回字段

| **result** | **value** | **type** |
| --- | --- | --- |
| hint | 笑话的内容 | string |
| formattype | text | string |

返回样例

```
    "result": {
        "hint": "爸爸：你要给妹妹做个好榜样。\n儿子：可是她不听我的啊。　\n爸爸：那就说明你是个没能力的人。\n儿子：那她也不听你的话啊！",
        "data": {
            "content": ""
        },
        "formatType": "text"
    }
```

