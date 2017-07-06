# 1. 服务简介

用户可以收听直播电台。电台资源来自喜马拉雅，电台类型包括国家台，省市台，以及网络台。类型范围包括音乐，新闻等15类电台。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| radioname | 电台名称 | 北京交通广播 |
| radio\_label | 电台类型 | 音乐 |
| location | 地理位置信息  \(包括省份和城市\) | 省份：河北、广东  城市：邢台、佛山 注：北京等直辖市属于省份还是城市随机 |

# 3.意图

\/GetRadio
电台点播意图。用户可以根电台名称直接点播，根据电台类型进行标签点播，根据地理位置信息进行地理位置点播或者不含任何槽位的模糊点播。

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

