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
|  | 唱首歌 |

返回字段

| **result** |  |  | **value** |
| --- | --- | --- | --- |
| hint |  |  | 准备播放 |
| data | album |  | 新地球 |
|  | artist |  | 林俊杰 |
|  | audio |  | http:\/\/dl.stream.qqmusic.qq.com\/C200004295Et37taLD.m4a?vkey=C07477C0B6B0ECF88D100FE3B64D763619D954BFA9C6DC8F0D784B9B1C006CC8EF59D603C417313906D7C10741AA3E543CEF725CBC488CAE&guid=6758412345&fromtag=30 |
|  | extra | type |  |
|  | image |  | https:\/\/y.gtimg.cn\/music\/photo\_new\/T002R300x300M000001IV22P1RDX7p.jpg?max\_age=2592000 |
|  | keywords |  | null |
|  | name |  | 可惜没如果 |
|  | resId |  | music:4037578 |
|  | sid |  | 3571606541-1499321247507 |
|  | start |  | 0 |
|  | trigger |  | voice |
|  | triggerId |  | null |
|  | type |  | MUSIC |
| formattype |  |  | audio |

---

\/Search

询问歌曲相关信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 这首歌是谁唱的 |

返回字段

| **result** | **value** |
| --- | --- |
| hint |  |

---

\/Next

更换一首相同关键词的歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 换一首 |

返回字段

| **result** |  |  | **value** |
| --- | --- | --- | --- |
| hint |  |  | 准备播放 |
| data | album |  | 新地球 |
|  | artist |  | 林俊杰 |
|  | audio |  | http:\/\/dl.stream.qqmusic.qq.com\/C200004295Et37taLD.m4a?vkey=C07477C0B6B0ECF88D100FE3B64D763619D954BFA9C6DC8F0D784B9B1C006CC8EF59D603C417313906D7C10741AA3E543CEF725CBC488CAE&guid=6758412345&fromtag=30 |
|  | extra | type |  |
|  | image |  | https:\/\/y.gtimg.cn\/music\/photo\_new\/T002R300x300M000001IV22P1RDX7p.jpg?max\_age=2592000 |
|  | keywords |  | null |
|  | name |  | 可惜没如果 |
|  | resId |  | music:4037578 |
|  | sid |  | 3571606541-1499321247507 |
|  | start |  | 0 |
|  | trigger |  | voice |
|  | triggerId |  | null |
|  | type |  | MUSIC |
| formattype |  |  | audio |

---

\/Pause

暂停当前播放的歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 暂停 |

返回字段

| **result** | **value** |
| --- | --- |
| hint |  |

---

\/ Resume

继续播放当前歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 继续 |

返回字段

| **result** |  |  | **value** |
| --- | --- | --- | --- |
| hint |  |  | 准备播放 |
| data | album |  | 新地球 |
|  | artist |  | 林俊杰 |
|  | audio |  | http:\/\/dl.stream.qqmusic.qq.com\/C200004295Et37taLD.m4a?vkey=C07477C0B6B0ECF88D100FE3B64D763619D954BFA9C6DC8F0D784B9B1C006CC8EF59D603C417313906D7C10741AA3E543CEF725CBC488CAE&guid=6758412345&fromtag=30 |
|  | extra | type |  |
|  | image |  | https:\/\/y.gtimg.cn\/music\/photo\_new\/T002R300x300M000001IV22P1RDX7p.jpg?max\_age=2592000 |
|  | keywords |  | null |
|  | name |  | 可惜没如果 |
|  | resId |  | music:4037578 |
|  | sid |  | 3571606541-1499321247507 |
|  | start |  | 0 |
|  | trigger |  | voice |
|  | triggerId |  | null |
|  | type |  | MUSIC |
| formattype |  |  | audio |

---

\/Replay
指重播当前歌曲（1遍）

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 继续 |

返回字段

| **result** |  |  | **value** |
| --- | --- | --- | --- |
| hint |  |  | 准备播放 |
| data | album |  | 新地球 |
|  | artist |  | 林俊杰 |
|  | audio |  | http:\/\/dl.stream.qqmusic.qq.com\/C200004295Et37taLD.m4a?vkey=C07477C0B6B0ECF88D100FE3B64D763619D954BFA9C6DC8F0D784B9B1C006CC8EF59D603C417313906D7C10741AA3E543CEF725CBC488CAE&guid=6758412345&fromtag=30 |
|  | extra | type |  |
|  | image |  | https:\/\/y.gtimg.cn\/music\/photo\_new\/T002R300x300M000001IV22P1RDX7p.jpg?max\_age=2592000 |
|  | keywords |  | null |
|  | name |  | 可惜没如果 |
|  | resId |  | music:4037578 |
|  | sid |  | 3571606541-1499321247507 |
|  | start |  | 0 |
|  | trigger |  | voice |
|  | triggerId |  | null |
|  | type |  | MUSIC |
| formattype |  |  | audio |

---

\/Exit
退出音乐场景

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 退出 |

返回字段

| **result** | **value** |
| --- | --- |
| hint |  |

