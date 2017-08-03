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
| &lt; StartCity &gt;+&lt;DestCity&gt;+&lt;date\_time&gt;+&lt;direciton&gt;+&lt;company&gt; | 给我订一张北京到上海明天上午10点之后的机票 |
| &lt; constellation &gt; +&lt;date&gt; | 天蝎座今天运势 |

