# 1. 服务简介

为用户提供各类音效的播放，比如老虎的咆哮声，自然音效等。

# 2. 意图

### \/Play

随机返回该topic相关的5条音效。

| **Slot Semantic Signatures** | **Description** | **Example** |

| --- | --- | --- |

| &lt;topic&gt; | 音效主题 | 我想听**人物**音效 |


_举例：数据部分_

```

    "results": [
        {
            "hint": "",
            "data": [
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/女人打寒颤.mp3",
                    "name": "女人打寒颤"
                },
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/女人呵音.mp3",
                    "name": "女人呵音"
                },
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/男人打寒颤.mp3",
                    "name": "男人打寒颤"
                },
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/两个女人一起说话.mp3",
                    "name": "两个女人一起说话"
                },
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/男人吹口哨声.mp3",
                    "name": "男人吹口哨声"
                }
            ],
            "formatType": "audio"
        }
    ]

```

---

### \/Play

返回关键字中存在该name的一条音效。

_举例：数据部分_

```

    "results": [
        {
            "hint": "",
            "data": [
                {
                    "audio": "http://mp3.yinxiao.com/abcdefg/1234567/upload/老虎吼声.mp3",
                    "name": "老虎吼声"
                }
            ],
            "formatType": "audio"
        }
    ]

```



