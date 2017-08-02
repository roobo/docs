# 1. 服务简介

可以为用户提供计算加减乘除，平方开方求倒数的功能。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| compute | 加减乘除的表达 | 7+9、八除以五 |
| number | 数字，用于求倒数，开方，平方 | 17 、二十 |

# 3.意图

\/Calc

处理加减乘除这四类基本运算

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;compute&gt; | 3加9等于几 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 计算结果 | string |
| data | arithmetic | 用户输入对应的表达式 | string |
|  | result | 计算结果 | string |

返回样例

```
    "result": {
        "hint": "等于12",
        "data": {
            "arithmetic": "(3)+(9)",
            "result": "12"
        }
    }
```

\/CalcNext

接着Calc意图，进行再次计算

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;compute&gt; | 再乘以5呢 |

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 计算结果 | string |
| data | arithmetic | 用户输入对应的表达式 | string |
|  | result | 计算结果 | string |

返回样例

```
    "result": {
        "hint": "等于60",
        "data": {
            "arithmetic": "(12)*(5)",
            "result": "60"
        }
    }
```

\/Exponent
计算平方

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;number&gt; | 16的平方是多少 |

