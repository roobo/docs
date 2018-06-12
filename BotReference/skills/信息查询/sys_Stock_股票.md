# 1. 服务简介

为用户提供股票价格，股票走势，股票K线图。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| stockid | 股票代码\(股票名字到股票code的一个映射\) | 中电控股-&gt;00002 |
| date | 日期 | 今天、明天、最近 |
| picturetype | 股票走势图的类型 | K线图、周K线图 |

# 3.意图

\/GetStock

询问某支股票某段时间内的价格，走向

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;stockid&gt; | 中国石化的股票 |
| &lt;stockid&gt;+&lt;date&gt; | 中国石化今天的股票 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 该股票的具体情况\(data中的内容\) | string |
| data | datetime | 日期时间 | string |
|  | gid | 股票编号 | string |
|  | image | 股票K线图url | string |
|  | increPer | 涨跌百分比 | string |
|  | increase | 涨跌额 | string |
|  | name | 股票名称 | string |
|  | nowPri | 当前股价 | string |
|  | todayMax | 今日最高股价 | string |
|  | todayMin | 今日最低股价 | string |
|  | todayStartPri | 今日开盘价 | string |
|  | traAmount | 成交额 | string |
|  | traNumber | 成交量 | string |
|  | yestodEndPri | 昨日股价 | string |

返回样例

```
    "results": [
        {
            "hint": "股票名称:百度，股票编号:bidu，当前价格:223.49，涨跌额:0.92，涨跌百分比0.41，时间:Aug 11 04:00PM EDT，今日开盘价:218.60，昨日收盘价:222.57，最高价:224.66，最低价:216.20，成交量:3.33M",
            "data": {
                "datetime": "2018-04-03 18:05:00",
                "gid": "bidu",
                "image": "http://image.sinajs.cn/newchartv5/usstock/min/bidu.gif",
                "increPer": "0.41",
                "increase": "0.92",
                "name": "百度",
                "nowPri": "223.49",
                "todayMax": "224.66",
                "todayMin": "216.20",
                "todayStartPri": "218.60",
                "traAmount": "-",
                "traNumber": "3.33M",
                "yestodEndPri": "222.57"
            }
        }
    ]
```

\/GetMarket

得到当前的大盘情况，包括上证，深证，沪证指数

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;&gt; | 股票大盘怎么样 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 主人，告诉我公司名称，可以帮你查询具体信息。 | string |
| data[] | datetime | 日期时间 | string |
|  | dealNum | 成交量 | string |
|  | dealPri | 成交额 | string |
|  | highPri | 最高价 | string |
|  | increPer | 涨跌百分比 | string |
|  | increase | 涨跌额 | string |
|  | index | 该数据结构在data数组中的下标 | string |
|  | lowPri | 最低价 | string |
|  | name | 股票名称 | string |
|  | nowPri | 当前股价 | string |
|  | todayMax | 今日最高股价 | string |
|  | todayMin | 今日最低股价 | string |
|  | todayStartPri | 今日开盘价 | string |

返回样例

```
    "results": [
        {
            "hint": "主人，告诉我公司名称，可以帮你查询具体信息。",
            "data": [
                {
                    "datetime": "2017-08-11 15:01:03",
                    "dealNum": "262.96M",
                    "dealPri": "2669.98亿",
                    "highPri": "3245.12",
                    "increPer": "-1.63",
                    "increase": "-53.21",
                    "index": 1,
                    "lowPri": "3200.75",
                    "name": "上证指数",
                    "nowPri": "3208.54",
                    "todayStartPri": "3237.92",
                    "yestodEndPri": "3261.75"
                },
                {
                    "datetime": "2017-08-11 15:05:03",
                    "dealNum": "22352.60M",
                    "dealPri": "2690.55亿",
                    "highPri": "10459.91",
                    "increPer": "-1.81",
                    "increase": "-189.29",
                    "index": 2,
                    "lowPri": "10281.63",
                    "name": "深证成指",
                    "nowPri": "10291.35",
                    "todayStartPri": "10407.33",
                    "yestodEndPri": "10480.64"
                },
                {
                    "datetime": "2017-08-11 15:01:03",
                    "dealNum": "1.50M",
                    "dealPri": "1610.83亿",
                    "highPri": "3700.49",
                    "increPer": "-1.85",
                    "increase": "-68.57",
                    "index": 3,
                    "lowPri": "3645.09",
                    "name": "沪深300",
                    "nowPri": "3647.35",
                    "todayStartPri": "3687.93",
                    "yestodEndPri": "3715.92"
                }
            ]
        }
    ]
```

\/GetPicture
返回用户查询的股票的K线图

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;stockid&gt;+&lt; picturetype &gt; | 中国石化的K线图 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 主人，为您找到该公司的股票走势图。 | string |
| data | image | 股票K线图的url | string |

返回样例

```
    "results": [
        {
            "hint": "主人，为您找到该公司的股票走势图。",
            "data": {
                "image": "http://image.sinajs.cn/newchart/daily/n/sh600028.gif"
            }
        }
    ]
```

