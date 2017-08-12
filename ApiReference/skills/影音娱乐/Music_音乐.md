
# 1. 服务简介

用户可以收听音乐。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| name | 歌曲名字 | 东风破 |
| artist | 作者 | 周杰伦 |
| keyword | 关键词 | 忧伤、情歌 |

# 3.意图

\/Play

播放用户想听的音乐

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;name&gt; | 东风破 |
| &lt;artist&gt; | 我要听周杰伦的歌 |
| &lt;keyword&gt; | 我要听忧伤的歌 |

返回字段说明，适用于以下其它意图

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | string | 提示语 | 准备播放 |
| data |  |  |  |  |
|  | album | string | 专辑名 | 传奇-刘德华 一起走过的日子 |
|  | artist | string | 艺术家 | 刘德华 |
|  | audio | string | 播放链接 | http://dwn.roo.bo/resource/music_bk/413/30261413.mp3 |
|  | hqAudio | string | 高质量播放链接 | http://dwn.roo.bo/resource/music_bk/413/30261413.mp3 |
|  | image | string | 专辑封面链接 | https://y.gtimg.cn/music/photo_new/T002R300x300M000003gkYbc2Athou.jpg?max_age=2592000 |
|  | hqImage | string | 高清专辑封面链接 | https://y.gtimg.cn/music/photo_new/T002R300x300M000003gkYbc2Athou.jpg?max_age=2592000 |
|  | name | string | 歌曲名 | 一起走过的日子 |
|  | resId | string | 歌曲名 | music:4147072 |
|  | start | int | 断点 | 需要上传播放状态 |
| formatType |  | string | 结果类型 | audio |

返回字段

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

\/Search

询问歌曲相关信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 这首歌是谁唱的 |



---

\/Next

用户主动更换一首相同关键词的歌曲

当前歌曲播放完成后自动播放下一首

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 换一首 |

返回字段

```
  "result": {
        "hint": "准备播放",
        "data": {
            "album": "十二新作",
            "artist": "周杰伦",
            "audio": "http://isure.stream.qqmusic.qq.com/C200000oW8J53xPhZA.m4a?vkey=838C86DFD53844D16B16C61346121D82C1DBFAB25EDF04F09B9C039187D51CA043EF36941B7AA4B79C05450F291957C5AEF8892E722EE646&guid=12347254&fromtag=50&uin=1152921504733674178",
            "extra": {
                "style": "流行"
            },
            "image": "http://i.gtimg.cn/music/photo/mid_album_300/q/i/003Ow85E3pnoqi.jpg",
            "keywords": null,
            "name": "明明就",
            "resId": "music:551242",
            "sid": "2419133446-1499329583202",
            "start": 0,
            "trigger": "voice",
            "triggerId": null,
            "type": "MUSIC"
        },
        "formatType": "audio"
    }
```

---

\/Pause

暂停当前播放的歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 暂停 |

---

\/ Resume

继续播放当前歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 继续 |

返回字段

```
    "result": {
        "hint": "继续播放",
        "data": {
            "album": "十二新作",
            "artist": "周杰伦",
            "audio": "http://isure.stream.qqmusic.qq.com/C200000oW8J53xPhZA.m4a?vkey=838C86DFD53844D16B16C61346121D82C1DBFAB25EDF04F09B9C039187D51CA043EF36941B7AA4B79C05450F291957C5AEF8892E722EE646&guid=12347254&fromtag=50&uin=1152921504733674178",
            "extra": {
                "style": "流行"
            },
            "image": "http://i.gtimg.cn/music/photo/mid_album_300/q/i/003Ow85E3pnoqi.jpg",
            "keywords": null,
            "name": "明明就",
            "resId": "music:551242",
            "sid": "2419133446-1499329583202",
            "start": 0,
            "trigger": "voice",
            "triggerId": null,
            "type": "MUSIC"
        },
        "formatType": "audio"
    }
```

---

\/Replay
指重播当前歌曲（1遍）

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 继续 |

返回字段

```
    "result": {
        "hint": "重新播放",
        "data": {
            "album": "十二新作",
            "artist": "周杰伦",
            "audio": "http://isure.stream.qqmusic.qq.com/C200000oW8J53xPhZA.m4a?vkey=838C86DFD53844D16B16C61346121D82C1DBFAB25EDF04F09B9C039187D51CA043EF36941B7AA4B79C05450F291957C5AEF8892E722EE646&guid=12347254&fromtag=50&uin=1152921504733674178",
            "extra": {
                "style": "流行"
            },
            "image": "http://i.gtimg.cn/music/photo/mid_album_300/q/i/003Ow85E3pnoqi.jpg",
            "keywords": null,
            "name": "明明就",
            "resId": "music:551242",
            "sid": "2419133446-1499329583202",
            "start": 0,
            "trigger": "voice",
            "triggerId": null,
            "type": "MUSIC"
        },
        "formatType": "audio"
    }
```

\/Exit

---

\/Exit
退出音乐场景

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 退出 |



