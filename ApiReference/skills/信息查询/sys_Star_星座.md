# 1. 服务简介

为用户提供星座运势以及星座匹配查询服务。资源来自星座屋 （[http:\/\/www.xzw.com\/](http://www.xzw.com/)） 。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| constellation | 星座 | 天蝎座 |
| date | 日期 | 今天\/明天 |
| gender | 性别 | 男\/女 |

# 3.意图

\*\*\*星座返回字段格式规整，在此进行统一说明

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 计算结果 | string |
| data | arithmetic | 用户输入对应的表达式 | string |
| formatType | | 返回值类型(text表示该场景返回值为文字类型) | string |

