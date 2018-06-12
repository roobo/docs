# 1.简介

资源播报类，指的是ROS.内容云资源的VUI点播与播放控制类需求。资源具备7个基本字段及9个标签的全方面描述能力。目前支持的分类包括音乐、儿歌、故事、电台，后续正在开发的包括诗词、笑话、有声书、小众音频等。

Examples

```
User: 播放东风破
User: 播放周杰伦的东风破
User: 播放睡前音乐
User: 播放80年代的歌
```

# 2.语义槽位描述

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| artist | 歌手 | 周杰伦 |
| name | 歌曲名 | 东风破 |
| album\_name | 歌单名 | 十一月的肖邦 |
|  |  |  |

# 3.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| :--- | :--- | :--- | :--- |
| album | string | 歌单名 | 爱如此神奇 |
| artist | string | 艺术家 | 刘德华 |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高清播放链接 | http://... |
| image | string | 专辑封面链接 | http://... |
| hqImage | string | 高清专辑封面链接 | http://... |
| length | int | 时长\(秒\) |  |
| name | string | 歌曲名 | 一起走过的日子 |
| playMode | string | \[循环\|顺序\] |  |
| resId | string | 资源标识 | music:... |
| size | int | 文件大小\(字节\) |  |
| start | int | 播放起始位置\(秒\) |  |

# 4.意图

### /Play

点播

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;name&gt; | 来首东风破 |
| &lt;artist&gt; | 我要听周杰伦的歌 |
| &lt;artist&gt;&lt;name&gt; | 我要听周杰伦的东风破 |

_举例：数据部分_

```
            "data": {
                "album": "叶惠美",
                "artist": "周杰伦",
                "audio": "http://dwn.roo.bo/resource/music_bk/775/30097775.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "image": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "length": 315,
                "name": "东风破",
                "playMode": "",
                "resId": "music:4041702",
                "sid": "3007738066-1528808220045",
                "size": 5050583,
                "start": 0,
                "type": "MUSIC"
            },
            "formatType": "audio"
```

---

### /Next

播控：下一首

_举例：数据部分_

```
            "data": {
                "album": "惊叹号",
                "artist": "周杰伦",
                "audio": "http://dwn.roo.bo/resource/music_bk/31026967.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://i.gtimg.cn/music/photo/mid_album_300/w/g/003KNcyk0t3mwg.jpg",
                "image": "http://i.gtimg.cn/music/photo/mid_album_300/w/g/003KNcyk0t3mwg.jpg",
                "length": 218,
                "name": "公主病",
                "playMode": "",
                "resId": "music:2941186",
                "sid": "1017128579-1528808288974",
                "size": 3504066,
                "start": 0,
                "type": "MUSIC"
            },
            "formatType": "audio"
```

---

### /Prev

播控：上一首

_举例：数据部分_

```
            "data": {
                "album": "叶惠美",
                "artist": "周杰伦",
                "audio": "http://dwn.roo.bo/resource/music_bk/775/30097775.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "image": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "length": 315,
                "name": "东风破",
                "playMode": "",
                "resId": "music:4041702",
                "sid": "3007738066-1528808333034",
                "size": 5050583,
                "start": 0,
                "type": "MUSIC"
            },
            "formatType": "audio"
```

---

### /Resume

播控：继续播放

_举例：数据部分_

```
            "data": {
                "album": "叶惠美",
                "artist": "周杰伦",
                "audio": "http://dwn.roo.bo/resource/music_bk/775/30097775.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "image": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "length": 315,
                "name": "东风破",
                "playMode": "",
                "resId": "music:4041702",
                "sid": "3007738066-1528808333034",
                "size": 5050583,
                "start": 0,
                "type": "MUSIC"
            },
            "formatType": "audio"
```

---

### /Replay

播控：指重播当前歌曲

_举例：数据部分_

```
            "data": {
                "album": "叶惠美",
                "artist": "周杰伦",
                "audio": "http://dwn.roo.bo/resource/music_bk/775/30097775.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "image": "http://y.gtimg.cn/music/photo_new/T002R300x300M000000MkMni19ClKG.jpg",
                "length": 315,
                "name": "东风破",
                "playMode": "",
                "resId": "music:4041702",
                "sid": "3007738066-1528808333034",
                "size": 5050583,
                "start": 0,
                "type": "MUSIC"
            },
            "formatType": "audio"
```

---

### /Pause

播控：暂停

---

### /Exit

播控：退出音乐场景

