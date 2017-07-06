# 1. 服务简介

用户可以询问当天以及往后15天的天气，风向，空气污染等情况。资源来自墨迹天气。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| date | 日期 | 今天、明天 |
| date-duration | 日期时间段 | 最近两天 |
| time | 时间 | 9点 |
| time\_period | 时间段 | 早上、傍晚 |
| weather\_condition | 天气状况 | 雨、雪、雾 |
| location | 地理位置信息 \(包括省份和城市\) | 省份：河北、广东 城市：邢台、佛山 注：北京等直辖市属于省份还是城市随机 |

# 3.意图

\/WeatherForADay
查询某天的天气状况

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;radioname&gt; | CNR中国之声 |
| &lt;radio\_label&gt; | 我要听音乐台 |
| &lt;position&gt; | 播放邢台的电台 |
|  | 我要听广播 |

返回字段

| **result** |  | **value** |
| --- | --- | --- |
| hint |  | 电台名称 |
| data | rate24\_aac\_url | 24码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8 |
|  | rate64\_aac\_url | 64码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8 |
|  | rate24\_ts\_url | 24码率ts播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8?transcode=ts |
|  | rate64\_ts\_url | 64码率ts播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8?transcode=ts |
| formattype |  | audio |

