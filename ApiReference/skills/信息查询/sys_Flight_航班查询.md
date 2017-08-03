# 1. 服务简介

为用户提供航班查询服务。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| company | 航空公司 | 中国国航 |
| date | 日期 | 今天\/明天 |
| StartCity | 出发城市 | 北京 |
| DestCity | 到达城市 | 福州 |
| time\_period | 时段 | 傍晚 |
| date\_time | 时间+日期 | 明天10点 |
| direction | 方向 | 前、后 |

# 3.意图

\/QueryFlight
查询机票

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt; StartCity &gt;+&lt;DestCity&gt;+&lt;date\_time&gt;+&lt;direciton&gt;+&lt;company&gt;\(不是所有条件都必须出现，可以为空，系统会进行多轮询问\) | 给我订一张北京到上海明天10点半之后的机票 |
| &lt; StartCity &gt;+&lt;DestCity&gt;+&lt;date&gt;+&lt;company&gt;\(不是所有条件都必须出现，可以为空，系统会进行多轮询问\) | 给我订一张北京到上海明天的机票 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 已为您查询到2017-08-04\(日期\)出发，从北京\(出发城市\)到福州\(到达城市\)的以下航班: | string |
| data\[\] |  arrival| 到达时间 | string |
|  | arrival| 到达时间 | string |
| | date| 出发日期 | string |
|  | departure|出发地 | string |
|  | number| 航班号 | string |
| | prince| 价格 | string |
| | time| 出发时间 | string |
| formatType |  | 回值类型\(text表示该场景返回值为文字类型\) | string |

返回样例

```
    "result": {
        "hint": "已为您查询到2017-08-04出发，从北京到福州的以下航班:",
        "data": [
            {
                "arrival": "00:50",
                "date": "2017-08-04",
                "departure": "PEK",
                "number": "HU7195",
                "price": 1010,
                "time": "22:05"
            },
            {
                "arrival": "23:30",
                "date": "2017-08-04",
                "departure": "PEK",
                "number": "SC1821",
                "price": 1210,
                "time": "20:35"
            },
            {
                "arrival": "23:30",
                "date": "2017-08-04",
                "departure": "PEK",
                "number": "CA1821",
                "price": 1240,
                "time": "20:35"
            }
        ],
        "formatType": "list"
    }
```

