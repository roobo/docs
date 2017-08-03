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
| data | fromAmount | 用户输入对应的表达式 | string |
|  | fromCode | 计算结果 | string |
| | fromName | 计算结果 | string |
| | toAmount | 计算结果 | string |
| | toCode | 计算结果 | string |
| | toName | 计算结果 | string |
|formatType | |prop| string |


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

