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

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  |股票大盘怎么样 |

返回样例
