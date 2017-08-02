# 1. 服务简介

可以为用户提供计算加减乘除，平方开方求倒数的功能。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| compute | 加减乘除的表达 | 7+9、八除以五 |
| number | 数字，用于求倒数，开方，平方 | 17 、二十 |

# 3.意图

\*\*\*计算器返回字段格式规整，在此进行统一说明

返回字段

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 计算结果 | string |
| data | arithmetic | 用户输入对应的表达式 | string |
|  | result | 计算结果 | string |

\/Calc

处理加减乘除这四类基本运算

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;compute&gt; | 3加9等于几 |

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

返回样例

```
    "result": {
        "hint": "等于64",
        "data": {
            "arithmetic": "(8)^(2)",
            "result": "64"
        }
    }
```

\/Sqrt
开方运算

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;number&gt; | 16开方等于几 |

返回样例

```
    "result": {
        "hint": "等于4",
        "data": {
            "arithmetic": "16开2次方",
            "result": "4"
        }
    }
```

\/Reciprocal

取倒数运算。对于0，返回0没有倒数。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;number&gt; | 7的倒数是几 |

返回样例

```
    "result": {
        "hint": "等于0.14",
        "data": {
            "arithmetic": "1/7",
            "result": "0.14"
        }
    }
```

