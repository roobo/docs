# 1. 服务简介

为用户提供货币兑换情况的查询，包括汇率及货币兑换。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| afcurrency | 需要兑换的货币 | 1美元 |
| tcurrency | 目标币种 | 人民币 |

# 3.意图

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | xx\(源货币数量\)xx\(源货币类型\)等于xx\(目的货币数量\)xx\(目的货币类型\)，例如：1美元等于6.73人民币 | string |
| data | fromAmount | 源货币数量 | string |
|  | fromCode | 源货币代码 | string |
|  | fromName | 源货币名称| string |
|  | toAmount |  转换后目标货币数量| string |
|  | toCode |转换后目标货币代码  | string |
|  | toName | 转换后目标货币名称 | string |
| formatType |  | prop | string |

\/Exchange

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

