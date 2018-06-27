# 1. 服务简介

资源播报类服务是AI云对外提供标准化服务之一。对外展示

包括：音乐/儿歌/故事，其有标准，后续持续引入

# 2.意图

### \/Play

播放用户想听的音乐

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;name&gt; | 来首东风破 |
| &lt;artist&gt; | 我要听周杰伦的歌 |
| &lt;artist&gt;&lt;name&gt; | 我要听周杰伦的东风破 |

_举例：数据部分_

```
    "results": [
        {
            "hint": "我们一起听 老师",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/lao_shi_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "老师",
                "resId": "aires:501950",
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
            "hint": "我们一起听 老师",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/lao_shi_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "老师",
                "resId": "aires:501950",
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
            "hint": "我们一起听 老师",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/lao_shi_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "老师",
                "resId": "aires:501950",
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
            "hint": "我们一起听 老师",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/lao_shi_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "老师",
                "resId": "aires:501950",
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
            "hint": "我们一起听 老师",
            "data": {
                "album": "",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/20160928/lao_shi_.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "老师",
                "resId": "aires:501950",
                "start": 0
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Exit

退出音乐场景

# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| name | 歌曲名字 | 东风破 |
| artist | 作者 | 周杰伦 |

# 4.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| album | string | 专辑名 | 传奇-刘德华 一起走过的日子 |
| artist | string | 艺术家 | 刘德华 |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高质量播放链接 | http://... |
| image | string | 专辑封面链接 | http://... |
| hqImage | string | 高清专辑封面链接 | http://... |
| name | string | 歌曲名 | 一起走过的日子 |
| resId | string | 资源标识 | music:... |
| start | int | 断点 | 需要上传播放状态 |



