
# 1. 服务简介

新闻

# 2.意图

### \/Play

播放用户想听的新闻

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;tag_topic&gt; | 我想听财经新闻 |
| &lt;keywords&gt; | 我想听九寨沟的新闻 |
| &lt;category&gt; | 我想听新闻摘要 |

_举例：数据部分_
```
   "results": [
        {
            "hint": "让我们一起听听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990ddc81215f.mp3",
                "name": "按不住的香港房价：中国买家纷纷离场 记录高位能持续到何时？",
                "tagTopic": "财经",
                "timestamp": 1502666186
            },
            "formatType": "audio"
        }
    ]
```

---


### \/Next
下一个

_举例：数据部分_
```
    "results": [
        {
            "hint": "让我们一起听听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990dbd280416.mp3",
                "name": "【听闻播报】热点城市房贷价升量跌料延续 刚需忧心被误伤",
                "tagTopic": "财经",
                "timestamp": 1502665693
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Prev
上一个

_举例：数据部分_
```
    "results": [
        {
            "hint": "让我们一起听听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990ddc81215f.mp3",
                "name": "按不住的香港房价：中国买家纷纷离场 记录高位能持续到何时？",
                "tagTopic": "财经",
                "timestamp": 1502666186
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Pause
暂停

---

### \/ Resume
继续播放

_举例：数据部分_
```
    "results": [
        {
            "hint": "主人，为你继续播放听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990ddc81215f.mp3",
                "name": "按不住的香港房价：中国买家纷纷离场 记录高位能持续到何时？",
                "tagTopic": "",
                "timestamp": 1502666186
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Replay
指重播当前新闻（1遍）

_举例：数据部分_

```
    "results": [
        {
            "hint": "主人，为你重复播放听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990ddc81215f.mp3",
                "name": "按不住的香港房价：中国买家纷纷离场 记录高位能持续到何时？",
                "tagTopic": "",
                "timestamp": 1502666186
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Change
换一批

_举例：数据部分_

```
    "results": [
        {
            "hint": "让我们一起听听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/5990d8af01b17.mp3",
                "name": "【听闻播报】韩国再度公开史料 证明日本曾非法强征“慰安妇”",
                "tagTopic": "国际",
                "timestamp": 1502664883
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Exit
退出新闻场景


# 3.槽位

| **Slot\_Key** | **Description** | **Main\_Description** | **Example** |
| --- | --- | --- | --- |
| tag_topic | 新闻主题 | 用于指定新闻主题 | 财经,科技 |
| keywords | 关键字 | 用于指定人物，事件，话题，地区等 | 刘德华 余额宝 爆炸 |
| category | 新闻类别 | 已经播放过摘要，需要再次收听时，需指明 | 摘要 快报 |

# 4.返回字段描述

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | string | 提示语 | 让我们一起听听闻 |
| data |  |  |  |  |
|  | audio | string | 新闻播放地址 | http://mp3.tingwen.me/data/upload/mp3/596e2a9d01ae2.mp3 |
|  | name | string | 新闻标题 | 软银集团和共享办公空间公司WeWork在日本成立合资公司 |
|  | tagTopic | string | 新闻主题 | 财经 |
|  | timestamp | int | 新闻产生时间戳 | 1502364363 |
| formatType |  | string | 结果类型 | audio |
