# 1. 服务简介
通过语音点播学科教材的内容，帮助孩子学习！
# 2. 槽位
| **Slot_key** | **Description** | **Example** |
| --- | --- | --- |
| age |	资源标签，年龄 |	我想听**6岁**的语文课文 |
| album | 专辑 | 我想听**一年级语文下册**的课文 |
| department | 资源标签，学部 | 我想听**小学**一年级语文课文 |
| grade | 资源标签，年级 | 我想听小学**一年级**语文课文 |
| keywords | 资源关键词 | 我想听关于**柳树**的课文 |
| name | 资源名称 | 我想听**吃水不忘挖井人**这篇课文 |
| number | 专辑点播中的集数 | 我想听一年级语文下册第**二**课的课文 |
| subject | 资源标签，学科 | 我想听小学一年级**语文**课文 |
| version | 资源标签，版本 | 我想听**人教版**小学一年级语文课文 |
| volume | 资源标签，册数 | 我想听人教版小学一年级语文**上册**的课文喝水不忘挖井人 |
# 3. 意图
注：返回该资源再所属专辑中以后的至多10条资源
### \/Play
播放相应音频
_举例：数据部分_
```
"results": [
        {
            "hint": "为您播放 乌鸦喝水",
            "data": {
                "album": "北师大版·语文（一年级上）",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/ai_bk/2017-04-26/wKgJXFk86wXgHgnaAAZreO6G_d0973.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://dwn.roo.bo//album/20170811/38da20d30661bf9ff99bccbe7495a6f8.png",
                "image": "http://dwn.roo.bo//album/20170811/38da20d30661bf9ff99bccbe7495a6f8.png",
                "length": 51,
                "name": "乌鸦喝水",
                "resId": "aires:1163827",
                "sid": "0-1513862035533",
                "size": 0,
                "start": 0,
                "type": "AUDIO"
            },
            "formatType": "audio"
        },
```
---
### \/Next
下一首
```
"results": [
        {
            "hint": "为您播放 大家都说普通话",
            "data": {
                "album": "北师大版·语文（一年级上）",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/ai_bk/2017-04-26/wKgJWVk861nDDxlDAAKrHi36Bqw515.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://dwn.roo.bo//album/20170811/38da20d30661bf9ff99bccbe7495a6f8.png",
                "image": "http://dwn.roo.bo//album/20170811/38da20d30661bf9ff99bccbe7495a6f8.png",
                "length": 21,
                "name": "大家都说普通话",
                "resId": "aires:1163833",
                "sid": "0-1513862035533",
                "size": 0,
                "start": 0,
                "type": "AUDIO"
            },
            "formatType": "audio"
        }`
```
---

### \/Pause
暂停

---
### \/Resume
继续
```
"results": [
        {
            "hint": "为您播放 i u ü y w yu",
            "data": {
                "album": "一年级语文上",
                "artist": "",
                "audio": "http://dwn.roo.bo/resource/ai_bk/wKgDZlWg4RLAMGNXABOGzmZxN2Y493.mp3",
                "extra": null,
                "hqAudio": "",
                "hqImage": "http://media.roo.bo/appimg/20161020_4d647c95a8d98677540a1a6f03ae8b47.png",
                "image": "http://media.roo.bo/appimg/20161020_4d647c95a8d98677540a1a6f03ae8b47.png",
                "length": 158,
                "name": "i u ü y w yu",
                "resId": "aires:507025",
                "sid": "0-1514860499446",
                "size": 0,
                "start": 0,
                "type": "AUDIO"
            },
            "formatType": "audio"
        }
```
---
### \/Prev
上一首

---
### \/Exit
退出

---
# 4. 返回字段描述
| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| album | string | 专辑名 | 北师大版·语文（一年级上） |
| artist | string | 艺术家 |  |
| audio | string | 播放链接 | http://... |
| hqAudio | string | 高质量播放链接 | http://... |
| image | string | 专辑封面链接 | https://... |
| hqImage | string | 高清专辑封面链接 | https://... |
| name | string | 作品名 | 大家都说普通话 |
| resId | string | 资源标识 | aires:1163833 |
| start | int | 断点 | 需要上传播放状态 |
| size | int | 文件大小(B) | 0 |
| sid | string | 相当于sessionid | 0-1513862035533 |
| length | int | 播放时长(s) | 21 |
| extra | string | 额外信息 | null |
| type | string | 资源类型 | AUDIO |
