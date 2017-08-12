
# 1. 服务简介

儿歌

# 2.意图

### \/Play

播放

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;name&gt; | 来首鹅妈妈俱乐部 |

_举例：数据部分_
```
    "results": [
        {
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://fdfs.xmcdn.com/group15/M03/91/77/wKgDaFY1eY3TTLkfAAOYIuzNaB4820.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "鹅妈妈俱乐部",
                "resId": "aires:510439",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Search
询问歌曲相关信息

_举例：数据部分_
```
    "results": [
        {
            "hint": "对不起,我还不知道这首歌是谁唱的",
            "formatType": "text"
        }
    ]
```


---

### \/Next
下一首

_举例：数据部分_
```
    "results": [
        {
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://fdfs.xmcdn.com/group15/M03/91/77/wKgDaFY1eY3TTLkfAAOYIuzNaB4820.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "鹅妈妈俱乐部",
                "resId": "aires:510439",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Prev
上一首

_举例：数据部分_
```
    "results": [
        {
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://fdfs.xmcdn.com/group15/M03/91/77/wKgDaFY1eY3TTLkfAAOYIuzNaB4820.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "鹅妈妈俱乐部",
                "resId": "aires:510439",
                "start": 0
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
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://fdfs.xmcdn.com/group15/M03/91/77/wKgDaFY1eY3TTLkfAAOYIuzNaB4820.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "鹅妈妈俱乐部",
                "resId": "aires:510439",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Replay
指重播当前歌曲（1遍）

_举例：数据部分_

```
    "results": [
        {
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://fdfs.xmcdn.com/group15/M03/91/77/wKgDaFY1eY3TTLkfAAOYIuzNaB4820.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "鹅妈妈俱乐部",
                "resId": "aires:510439",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Exit
退出儿歌场景

# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| name | 儿歌名字 | 鹅妈妈俱乐部 |

# 4.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| album | string | 专辑名 | 贝瓦儿歌 |
| artist | string | 艺术家 |  |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高质量播放链接 | http://... |
| image | string | 专辑封面链接 | http://... |
| hqImage | string | 高清专辑封面链接 | http://... |
| name | string | 歌曲名 | 拔萝卜 |
| resId | string | 歌曲名 | aires:... |
| start | int | 断点 | 需要上传播放状态 |
