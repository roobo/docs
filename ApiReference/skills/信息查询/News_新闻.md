
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
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d04b4991af.mp3",
                "tagTopic": "科技",
                "timestamp": 1502414039,
                "title": "【创业邦早报】传央行要求删除“无现金”宣传字眼，总行回应；锤子炮轰阿里差点被它害死，阿里回怼",
                "type": "audio"
            },
            "formatType": "news"
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
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d5b8576e55.mp3",
                "tagTopic": "时政",
                "timestamp": 1502436304,
                "title": "【央广评论】打击传销,要关注传销人员何去何从?",
                "type": "audio"
            },
            "formatType": "news"
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
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d1e3f426eb.mp3",
                "tagTopic": "财经",
                "timestamp": 1502420545,
                "title": "【听闻财经通】“共有产权房”横空出世 刚需们福利到来了？",
                "type": "audio"
            },
            "formatType": "news"
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
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d1e3f426eb.mp3",
                "tagTopic": "财经",
                "timestamp": 1502420545,
                "title": "【听闻财经通】“共有产权房”横空出世 刚需们福利到来了？",
                "type": "audio"
            },
            "formatType": "news"
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
            "hint": "主人，为你继续播放听闻",
            "data": {
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d1e3f426eb.mp3",
                "tagTopic": "财经",
                "timestamp": 1502420545,
                "title": "【听闻财经通】“共有产权房”横空出世 刚需们福利到来了？",
                "type": "audio"
            },
            "formatType": "news"
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
                "audio": "http://mp3.tingwen.me/data/upload/mp3/598d4ade2db77.mp3",
                "tagTopic": "国际",
                "timestamp": 1502431991,
                "title": "杜特尔特支持中国主导自贸协定：TPP是消失的梦",
                "type": "audio"
            },
            "formatType": "news"
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
|  | tagTopic | string | 新闻主题 | 财经 |
|  | timestamp | int | 新闻产生时间戳 | 1502364363 |
|  | title | string | 新闻标题 | 软银集团和共享办公空间公司WeWork在日本成立合资公司 |
|  | type | string | 数据类型 | audio |
| formatType |  | string | 结果类型 | news |
