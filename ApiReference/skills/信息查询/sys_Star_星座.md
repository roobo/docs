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

返回样例

```
    "result": {
        "hint": "整体运势：今天建议就将感情的心思用在工作上，只要认真对待，必定有很好的收获，部分人还有晋升的机会。在爱情上用情过深，很容易会导致自己受伤害。身体上会有不适的情况，要多抽时间做做运动。爱情运势：感情颇为不顺，易受爱情所困。事业学业：头脑运作加快，懂得用智慧做事。财富运势：金钱流动性较快，一定要量入为出才好。健康运势：温度变化，注意环境温差对身体的影响。",
        "data": {
            "content": ""
        },
        "formatType": "text"
    }
```

