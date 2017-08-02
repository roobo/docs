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
