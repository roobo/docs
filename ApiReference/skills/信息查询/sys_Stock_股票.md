# 1. 服务简介

为用户提供股票价格，股票走势，股票图形。

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

返回样例

```
    "result": {
        "hint": "股票名称:中国石化，股票编号:sh600028，当前价格:6.14，涨跌额:-0.08，涨跌百分比-1.29，时间:2017-08-02 15:00:00，今日开盘价:6.19，昨日收盘价:6.22，最高价:6.20，最低价:6.11，成交量:1.52M",
        "data": {
            "datetime": "2017-08-02 15:00:00",
            "gid": "sh600028",
            "image": "http://image.sinajs.cn/newchart/min/n/sh600028.gif",
            "increPer": "-1.29",
            "increase": "-0.08",
            "name": "中国石化",
            "nowPri": "6.14",
            "todayMax": "6.20",
            "todayMin": "6.11",
            "todayStartPri": "6.19",
            "traAmount": "9.37亿",
            "traNumber": "1.52M",
            "yestodEndPri": "6.22"
        }
    }
```

\/GetMarket

得到当前的大盘情况，包括上证，深证，沪证指数

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 股票大盘怎么样 |

返回样例

```
    "result": {
        "hint": "主人，告诉我公司名称，可以帮你查询具体信息。",
        "data": [
            {
                "datetime": "2017-08-02 15:10:03",
                "dealNum": "266.73M",
                "dealPri": "2793.52亿",
                "highPri": "3305.43",
                "increPer": "-0.23",
                "increase": "-7.58",
                "index": 1,
                "lowPri": "3282.04",
                "name": "上证指数",
                "nowPri": "3285.06",
                "todayStartPri": "3288.52",
                "yestodEndPri": "3292.64"
            },
            {
                "datetime": "2017-08-02 15:10:03",
                "dealNum": "24843.68M",
                "dealPri": "3051.80亿",
                "highPri": "10557.48",
                "increPer": "-0.53",
                "increase": "-56.01",
                "index": 2,
                "lowPri": "10461.95",
                "name": "深证成指",
                "nowPri": "10469.34",
                "todayStartPri": "10526.00",
                "yestodEndPri": "10525.35"
            },
            {
                "datetime": "2017-08-02 15:10:03",
                "dealNum": "1.72M",
                "dealPri": "1893.37亿",
                "highPri": "3784.35",
                "increPer": "-0.25",
                "increase": "-9.53",
                "index": 3,
                "lowPri": "3759.28",
                "name": "沪深300",
                "nowPri": "3760.85",
                "todayStartPri": "3768.19",
                "yestodEndPri": "3770.38"
            }
        ]
    }
```

\/GetPicture
返回用户查询的股票的K线图

返回样例

```
    "result": {
        "hint": "主人，为您找到该公司的股票走势图。",
        "data": {
            "image": "http://image.sinajs.cn/newchart/daily/n/sh600028.gif"
        }
    }
```

