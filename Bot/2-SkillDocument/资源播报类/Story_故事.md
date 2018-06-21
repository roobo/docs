
# 1. 服务简介

故事

# 2.意图

### \/Play

播放

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;&gt; | 讲个故事 |
| &lt;name&gt; | 来首灰姑娘 |

_举例：数据部分_
```
    "results": [
        {
            "hint": "准备播放",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/hui_gu_niang_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "灰姑娘",
                "resId": "aires:515796",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Search
询问故事相关信息

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
                "audio": "http://dwn.roo.bo/resource/20160928/hui_gu_niang_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "灰姑娘",
                "resId": "aires:515796",
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
                "audio": "http://dwn.roo.bo/resource/20160928/hui_gu_niang_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "灰姑娘",
                "resId": "aires:515796",
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
                "audio": "http://dwn.roo.bo/resource/20160928/hui_gu_niang_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "灰姑娘",
                "resId": "aires:515796",
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
                "audio": "http://dwn.roo.bo/resource/20160928/hui_gu_niang_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "灰姑娘",
                "resId": "aires:515796",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Exit
退出故事场景

# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| name | 故事名字 | 灰姑娘 |

# 4.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| album | string | 专辑名 | 凯叔讲故事 |
| artist | string | 艺术家 |  |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高质量播放链接 | http://... |
| image | string | 专辑封面链接 | http://... |
| hqImage | string | 高清专辑封面链接 | http://... |
| name | string | 故事名 | 西游记 |
| resId | string | 资源标识 | aires:... |
| start | int | 断点 | 需要上传播放状态 |
