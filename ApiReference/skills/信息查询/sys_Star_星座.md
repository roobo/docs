# 1. 服务简介

为用户提供星座运势以及星座匹配查询服务。资源来自星座屋 （[http:\/\/www.xzw.com\/](http://www.xzw.com/)） 。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| constellation | 星座 | 天蝎座 |
| date | 日期 | 今天\/明天 |
| gender | 性别 | 男\/女 |

# 3.意图

\/Horoscope

查询星座运势。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt; constellation &gt; | 天蝎座运势 |
| &lt; constellation &gt; +&lt;date&gt; | 天蝎座今天运势 |

返回字段

| **result** | **value** | **type** |
| --- | --- | --- |
| hint | 查询到的该星座的运势 | string |
| formatType | 回值类型\(text表示该场景返回值为文字类型\) | string |

\| **result** \|  \| **value** \| **type** \|
\| --- \| --- \| --- \| --- \|
\| hint \|  \| 查询到的该星座的运势 \| string \|
\| formatType \|  \| 返回值类型\(text表示该场景返回值为文字类型\) \| string \|

