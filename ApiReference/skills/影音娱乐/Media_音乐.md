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

播放用户要的音乐

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

\/Pause

暂停当前播放的歌曲

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 暂停 |

# 4. 点播具体策略

## 1、点播策略

\(1\)GetRadio\(直接点播\)

模板：我要听\[@sys.radioid:name\]

预期结果：如果有该电台，直接播放，没有返回没找到资源

\(2\)GetRadio\(标签点播\)

模板：我要听[@sys.radio\_label:label](我要听音乐台)

预期结果：根据用户地理位置优先出资源，例：用户在邢台，优先出邢台的音乐台，如果邢台没有音乐台，则出河北的音乐台，如果省级也没有，打通全国标签，在全国范围内查询，按top15随机播放

如果没有地理位置信息，找国家级该类型电台

\(3\)GetRadio\(地理位置点播\)

模板：我要听\[@sys.city:city\]的电台\(我要听邢台的电台\)

预期结果：如果该城市有电台，就按top5\(可不足\)随机播放，如果当地没有电台，则返回没找到，不会随机出资源

\(4\)GetRadio\(随机播放\)

模板：我要听电台\/广播

预期结果：如果该用户曾经听过电台，则取该用户的历史信息，直接播放

如果该用户没有使用过电台，则根据用户的地理位置信息获取当地top15电台，随机播放其中一个，市级没有电台找省级，省级没有找国家级

## 2、播放控制策略（下一首）

\(1\)Next\(直接点播\)

预期：根据用户的地理位置信息获取当地top15电台，随机播放其中一个，市级没有电台找省级，省级没有找国家级，去重

\(2\)Next\(标签点播\)

预期：不关心地理信息，在该标签下的top15随机选择一个，去重

\(3\)Next\(地理位置点播\)

预期：如果当地电台多于一个，去重循环，如果当地电台只有一个，循环播放，不考虑重复

\(4\)Next\(随机点播\)

预期：同直接点播

