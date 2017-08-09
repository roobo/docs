# 1. 服务简介

用户可以收听直播电台。电台资源来自喜马拉雅，电台类型包括国家台，省市台，以及网络台。类型范围包括音乐，新闻等15类电台。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| radioname | 电台名称 | 北京交通广播 |
| radio\_label | 电台类型 | 音乐 |
| location | 地理位置信息  \(包括省份和城市\) | 省份：河北、广东  城市：邢台、佛山 注：北京等直辖市属于省份还是城市随机 |

# 3.意图

\/Play
电台点播意图。用户可以根电台名称直接点播，根据电台类型进行标签点播，根据地理位置信息进行地理位置点播或者不含任何槽位的模糊点播。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;radioname&gt; | CNR中国之声 |
| &lt;radio\_label&gt; | 我要听音乐台 |
| &lt;position&gt; | 播放邢台的电台 |
|  | 我要听广播 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 电台名称 | string |
| data | name | 电台名称 | string |
|  | audio | 24码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8 | string |
|  | hqAudio | 64码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8 | string |
| formattype |  | audio | string |

返回样例

```
    "result": {
        "hint": "邢台爱尚986",
        "data": {
            "audio": "http://live.xmcdn.com/live/1126/24.m3u8",
            "hqAudio": "http://live.xmcdn.com/live/1126/64.m3u8",
            "name": "邢台爱尚986"
        },
        "formatType": "audio"
    }
```

---

\/Next
更换电台意图。根据用户上次点播的意图，为用户提供不同的换台策略。详见4.具体点播策略

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 换一个电台 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 电台名称 | string |
| data | name | 电台名称 | string |
|  | audio | 24码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/24.m3u8 | string |
|  | hqAudio | 64码率acc播放地址，如：http:\/\/live.xmcdn.com\/live\/93\/64.m3u8 | string |
| formattype |  | audio | string |

返回样例

```
    "result": {
        "hint": "邢台县人民广播电台",
        "data": {
            "rate24_aac_url": "http://live.xmcdn.com/live/1132/24.m3u8",
            "rate24_ts_url": "http://live.xmcdn.com/live/1132/24.m3u8?transcode=ts",
            "rate64_aac_url": "http://live.xmcdn.com/live/1132/64.m3u8",
            "rate64_ts_url": "http://live.xmcdn.com/live/1132/64.m3u8?transcode=ts"
        },
        "formatType": "audio"
    }
```

---

\/GetPlayingProgram
查询当前电台正在播放的节目。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 现在播放的是什么节目啊 |

返回字段

| **result** | **value** | **type** |
| --- | --- | --- |
| hint | 有节目内容： 当前播放的是“radioname”的《XXXX》           无节目内容： 没有找到相关节目内容 | string |
| formattype | text | string |

返回样例

```
    "result": {
        "hint": "当前播放的是CRI环球旅游广播的益游未尽",
        "formatType": "text"
    }
```

---

\/GetAnchor
 查询当前节目的主播列表。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 主播是谁 |

返回字段

| **result** | **value** | **type** |
| --- | --- | --- |
| hint | 查到主播信息： 主播是xxx                                                 没查到主播： 没有查到主播信息 | string |
| formattype | text | string |

返回样例

```
    "result": {
        "hint": "主播是璟炜",
        "formatType": "text"
    }
```

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

