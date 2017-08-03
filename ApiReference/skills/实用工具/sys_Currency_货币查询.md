# 1. 服务简介

为用户提供货币兑换情况的查询，包括汇率及货币兑换。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| unit\_currency | 货币数量+货币类型 | 1美元、3块钱 |
| currency | 货币类型 | 人民币、美元 |

# 3.意图

\*\*\*由于Exchange和GetExchangeRate返回字段相同，在此统一说明

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

\/Exchange

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;unit\_currency&gt;+&lt;currency&gt; | 2美元等于多少人民币 |

返回样例

```
    "result": {
        "hint": "2美元等于13.46人民币",
        "data": {
            "fromAmount": "2",
            "fromCode": "USD",
            "fromName": "美元",
            "toAmount": "13.46",
            "toCode": "CNY",
            "toName": "人民币"
        },
        "formatType": "prop"
    }
```

\/GetExchangeRate

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;afcurrency&gt;+&lt;tcurrency&gt; | 2美元等于多少人民币 |

返回样例

```
   "result": {
        "hint": "1美元等于6.73人民币",
        "data": {
            "fromAmount": "1",
            "fromCode": "USD",
            "fromName": "美元",
            "toAmount": "6.73",
            "toCode": "CNY",
            "toName": "人民币"
        },
        "formatType": "prop"
    }

```

