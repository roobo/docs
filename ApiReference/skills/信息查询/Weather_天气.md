
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

返回字段说明

用户查询的是某一天的天气，所以返回的data中是一个结构体，存放温度，风向等信息

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | 天气情况 | string | 北京明天，气温23度到30度，东南风2级转东风3级，阵雨 |
| data |  |  |  |  |
|  | alter | 预警 | string |  |
|  | city | 城市 | string | 北京 |
|  | date | 日期 | string | 2017-08-01 |
|  | focus | 查询关键词 | string | rain |
|  | humidity | 湿度 | string | 31 |
|  | index | 返回天气天数索引 | string | 1 |
|  | maxTemp | 最高温度 | string | 30 |
|  | minTemp | 最低温度 | string | 23 |
|  | pm25 | pm25值 | string | 24 |
|  | temperature | 温度 | string | 37 |
|  | weather | 天气 | string | 阵雨 |
|  | windDay | 白天风向 | string | 东南风 |
|  | windDayLevel | 白天风力 | string | 2 |
|  | windDir | 转向 | string | 东北风 |
|  | windLevel | 风力 | string | 2 |
|  | windNight | 夜晚风向 | string | 东风 |
|  | windNightLevel | 夜晚风力 | string | 3 |

返回字段
```
    "result": {
        "hint": "北京明天，气温23度到30度，东南风2级转东风3级，阵雨",
        "data": [
            {
                "alter": "",
                "city": "北京",
                "date": "2017-08-01",
                "focus": "rain",
                "humidity": "",
                "index": 1,
                "maxTemp": "30",
                "minTemp": "23",
                "pm25": "",
                "temperature": "",
                "weather": "阵雨",
                "windDay": "东南风",
                "windDayLevel": "2",
                "windDir": "",
                "windLevel": "",
                "windNight": "东风",
                "windNightLevel": "3"
            }
        ]
    }
```
\/WeatherForDays
查询某一段时间的天气状况

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;location&gt; + &lt;date&gt; + &lt;weather\_condition&gt; | 邢台这两天有雨么 |

返回字段说明及示例同上

根据用户查询的天数，data中返回对应数量的结构体

第一个data中index字段为

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
|  | index | 返回天气天数索引 | string | 1 |

第二个data中index字段为

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
|  | index | 返回天气天数索引 | string | 2 |
