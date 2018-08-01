# 1.服务背景

资源播报类服务是AI云对外提供标准化服务之一。通过内容云对播报类资源（音乐/儿歌/故事，etc）进行维护，进而可以通过VUI方式进行点播。开发者针对此类场景只需接入自己的资源即可，无需进行相关技能的研发。

## 2. 槽位

| Slot\_Key | Description | Main\_Application | normType | Example |
| --- | --- | --- | --- |
| artist | 艺术家 | | StrArray | 周杰伦 |
| name | 资源名 | | StrArray | 红尘客栈 |
| album_name | 专辑名 | | StrArray | 十一月的肖邦 |

# 3.意图

## 3.1 Play\_播放

意图关键词：[播放][音乐|故事|儿歌]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 意图关键词：+&lt;artist&gt;&lt;name&gt; | 播放刘德华的忘情水 |

## 3.3 Next\_下一首

## 3.4 Replay\_重播

## 3.5 Resume\_继续播放

## 3.6 Pause\_暂停

## 3.7 Exit\_退出

# 4.返回结果

## 4.1 formatType=="audio", data内容

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
| start | int | 播放起始位置，单位秒 | 需要上传播放状态 |
| size | int | 文件大小，单位字节 |  |
| length | int | 时长，单位秒 |  |
| playMode | string | 播放模式 | [repeat,random] |

## 4.2 formatType=="", data为空
