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
| &lt;location&gt; + &lt;date&gt; + &lt;weather\_condition&gt; | 北京明天有雨么 |
| &lt;location&gt; + &lt;date&gt; + &lt;time&gt; + &lt;weather\_condition&gt; | 邢台明天9点有雨么 |
| &lt;location&gt; + &lt;date&gt; + &lt;time\_period&gt; + &lt;weather\_condition&gt; | 邢台明天傍晚有雨么 |

返回字段

用户查询的是某一天的天气，所以返回的data中是一个结构体，存放温度，风向等信息

| **result** |  | **value** |
| --- | --- | --- |
| hint |  | 天气情况 |
| data | alter |  |
|  | city | 邢台 |
|  | date | 2017-07-06 |
|  | focus | rain |
|  | humidity |  |
|  | index |  |
|  | maxTemp | 28 |
|  | minTemp | 21 |

