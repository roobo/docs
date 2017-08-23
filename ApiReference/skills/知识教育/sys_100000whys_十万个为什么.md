
# 1. 服务简介

十万个为什么

# 2.意图

### \/Play

播放用户想听的十万个为什么资源

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;category&gt; | 十万个为什么 |
| &lt;name&gt; | 为什么荷花出淤泥而不染 |

_举例：数据部分_
```
    "results": [
        {
            "hint": "让我们一起听冯巩,牛群的办晚会",
            "data": {
                "album": "",
                "artist": "冯巩,牛群",
                "audio": "http://cdn5.lizhi.fm/audio/2014/09/27/14705754079396998_hd.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "办晚会",
                "resId": "aires:65172",
                "start": 0,
                "type": "相声"
            },
            "formatType": "audio"
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
            "hint": "让我们一起听冯巩,牛群的开心一刻",
            "data": {
                "album": "",
                "artist": "冯巩,牛群",
                "audio": "http://cdn5.lizhi.fm/audio/2014/09/27/14705261500109702_hd.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "开心一刻",
                "resId": "aires:65170",
                "start": 0,
                "type": "相声"
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
            "hint": "让我们一起听冯巩,牛群的办晚会",
            "data": {
                "album": "",
                "artist": "冯巩,牛群",
                "audio": "http://cdn5.lizhi.fm/audio/2014/09/27/14705754079396998_hd.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "办晚会",
                "resId": "aires:65172",
                "start": 0,
                "type": "相声"
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
            "hint": "主人，为你继续播放办晚会",
            "data": {
                "album": "",
                "artist": "冯巩,牛群",
                "audio": "http://cdn5.lizhi.fm/audio/2014/09/27/14705754079396998_hd.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "办晚会",
                "resId": "aires:65172",
                "start": 0,
                "type": "相声"
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
            "hint": "主人，为你继续播放办晚会",
            "data": {
                "album": "",
                "artist": "冯巩,牛群",
                "audio": "http://cdn5.lizhi.fm/audio/2014/09/27/14705754079396998_hd.mp3",
                "hqAudio": "",
                "hqImage": "",
                "image": "",
                "name": "办晚会",
                "resId": "aires:65172",
                "start": 0,
                "type": "相声"
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Exit
退出小众音频场景

# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| name | 音频名字 | 十五的月亮 |
| artist | 作者 | 冯巩 |

# 4.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| album | string | 专辑名 |  |
| artist | string | 艺术家 | 赵本山,高秀敏,范伟 |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高质量播放链接 | http://... |
| image | string | 专辑封面链接 | https://... |
| hqImage | string | 高清专辑封面链接 | https://... |
| name | string | 作品名 | 功夫 |
| resId | string | 资源标识 | aires:1121072 |
| start | int | 断点 | 需要上传播放状态 |
