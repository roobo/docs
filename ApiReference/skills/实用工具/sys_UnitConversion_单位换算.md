# 1. 服务简介

为用户提供单位换算，包括长度，重量，面积，体积\/容积，速度，温度。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| unit\_num | 数量+单位 | 1平米、3摄氏度 |
| unit | 单位 |升、km/h |

# 3.意图

\*\*\*由于涉及到的单位种类较多，询问逻辑和返回字段都是一样的，在此抽象成一个Convert函数

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | xx\(源货币数量\)xx\(源货币类型\)等于xx\(目的货币数量\)xx\(目的货币类型\)，例如：1美元等于6.73人民币 | string |
| data | fromAmount | 源货币数量 | string |
|  | fromCode | 源货币代码 | string |
|  | fromName | 源货币名称 | string |
|  | toAmount | 转换后目标货币数量 | string |
|  | toCode | 转换后目标货币代码 | string |
|  | toName | 转换后目标货币名称 | string |
| formatType |  | prop | string |

\/Convert

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;unit\_num&gt;+&lt;unit&gt; | 2美元等于多少人民币 |
|  |  |

