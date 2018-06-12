# 1. 服务简介

为用户提供单位换算，包括长度，重量，面积，体积\/容积，速度，温度。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| unit\_num | 数量+单位 | 1平米、3摄氏度 |
| unit | 单位 | 升、km\/h |

# 3.意图

\*\*\*由于涉及到的单位种类较多，询问逻辑和返回字段都是一样的，在此抽象成一个Convert函数

\/Convert

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;unit\_num&gt;+&lt;unit&gt; | 1.5米等于多少厘米 |
| &lt;unit&gt; | 那毫米呢\(多轮，接上次询问\) |
| &lt; unit&gt; + &lt; unit&gt; | 米等于多少纳米\(单位之间的转换\) |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | xx\(源单位数量\)xx\(源单位类型\)等于xx\(目的单位数量\)xx\(目的单位类型\)，例如：1米等于100毫米 | string |
| data | fromAmount | 源单位数量 | string |
|  | fromCode | 源单位代码 | string |
|  | fromName | 源单位名称 | string |
|  | toAmount | 转换后目标单位数量 | string |
|  | toCode | 转换后目标单位代码 | string |
|  | toName | 转换后目标单位名称 | string |

返回样例

```
    "result": {
        "hint": "2.3米等于2300000微米",
        "data": {
            "fromAmount": "2.3",
            "fromCode": "m",
            "fromName": "米",
            "toAmount": "2300000",
            "toCode": "um",
            "toName": "微米"
        }
    }
```

