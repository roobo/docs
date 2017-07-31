# 1. 服务简介

波鲁鲁故事机的需求，告知故事机在某个时间点关机，故事机到点关机。产品@袁仁富。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| date | 日期\(不带时间\) | 三天后 |
| date\_time | 时间（必需）+日期（不必需） | 明天10点、10分钟后 |

# 3.意图

\/Play

电台点播意图。用户可以根电台名称直接点播，根据电台类型进行标签点播，根据地理位置信息进行地理位置点播或者不含任何槽位的模糊点播。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;date&gt; | CNR中国之声 |
| &lt;radio\_label&gt; | 我要听音乐台 |
| &lt;position&gt; | 播放邢台的电台 |
|  | 我要听广播 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 电台名称 | string |
| data | rate24\_aac\_url | 24码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8 | string |
|  | rate64\_aac\_url | 64码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8 | string |
|  | rate24\_ts\_url | 24码率ts播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8?transcode=ts | string |
|  | rate64\_ts\_url | 64码率ts播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8?transcode=ts | string |
| formattype |  | audio | string |

