# 1. 服务简介

用户通过语音方式和机器人交互，查询时间／日期／星期等信息。

# 2.意图

### \/GetTime

获取时间信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;city&gt; | 北京 |
| &lt;timequantum&gt; | 晚上 |

_举例_：

**query**: 北京现在是晚上几点了

```
"results": [
    {
      "hint": "北京现在是晚上8点22分",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "city": "北京",
        "timestamp": 1539087779,
        "timezone": "Asia/Shanghai"
      }
    }
  ]
```

### \/GetDate

获取日期信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;date&gt; | 今天 |
| &lt;lunar&gt; | 阴历 |

分两种情况：

**a.获取阳历日期**

_举例_：

**query**: 今天是几号

```
"results": [
    {
      "hint": "今天是2017-05-17，星期三",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "date": "2017-05-17",
        "lunardate": "四月廿二",
        "solarterm": "",
        "weekday": "星期三"
      }
    }
  ]
```

**b.获取阴历日期**

_举例_：

**query**: 今天是阴历几号

```
"results": [
    {
      "hint": "今天是农历九月初一",
      "emotions": [
        {
          "type": "answer",
          "level": 14,
          "code": "O002"
        }
      ],
      "data": {
        "date": "2018-10-09",
        "lunardate": "九月初一",
        "solarterm": "",
        "weekday": "星期二"
      }
    }
  ]
```

### \/GetWeekDay

获取星期信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;date&gt; | 今天 |
| &lt;weekday&gt; | 星期 |

_举例_：

**query**: 今天是星期几

```
"results": [
    {
      "hint": "今天是星期二",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "date": "2018-10-09",
        "lunardate": "九月初一",
        "solarterm": "",
        "weekday": "星期二"
      }
    }
  ]
```

### \/GetYear

获取年份信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;year&gt; | 今年 |

_举例_：

**query**: 今年是哪一年

```
"results": [
    {
      "hint": "2018-02-16之前是丁酉年鸡年，之后是戊戌年狗年",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "date": "",
        "lunardate": "",
        "solarterm": "",
        "weekday": ""
      }
    }
  ]
```

### \/GetMonth

获取月份信息

_举例_：

**query**: 现在几月份

```
  "results": [
    {
      "hint": "现在是十月份,秋季呢",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "date": "",
        "lunardate": "",
        "month": "10",
        "season": "秋季",
        "solarterm": "",
        "weekday": "",
        "year": "2018"
      }
    }
  ]
```

### \/GetDiffDay

获取相差的天数

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;enddate&gt; | 春节 |

_举例_：

**query**: 离春节还有多少天

```
"results": [
    {
      "hint": "今天距春节还有119天",
      "emotions": [
        {
          "type": "answer",
          "level": 0,
          "code": "A001"
        }
      ],
      "data": {
        "delta": 119
      }
    }
  ]
```

### \/GetDiffDay

获取指定日期的风俗习惯

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;date&gt; | 端午节 |

_举例_：

**query**: 端午节有什么风俗

```
"results": [
    {
      "hint": "端午节的习俗有赛龙舟，吃粽子，挂艾草，沐兰汤，放风筝，拴五色丝线哦",
      "emotions": [
        {
          "type": "answer",
          "level": 14,
          "code": "O002"
        }
      ]
    }
  ]
```

# 3. 返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Desc** | **Field\_Example** |
| --- | --- | --- | --- |
| delta | int | 相差的天数 | 112 |
| city | string | 城市信息 | 北京 |
| timestamp | string | 时间对应的时间戳 | 1539087779 |
| timezone | string | 城市所对应的时区 | Asia/Shanghai |
| date | string | 阳历日期 | 2017-05-17 |
| lunardate | string | 阴历日期 | 四月廿二 |
| weekday | string | 星期几 | 星期三 |
| solarterm | string | 节气 | 立夏 |
| season | string | 季节 | 秋季 |
| year | string | 年份 | 2018 |
| month | string | 月份 | 10 |


