
# 1. 服务简介

节假日查询

# 2.意图

### \/GetHolidayPlan

获取用户查询节日或者月份的放假安排

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;holiday&gt; | 国庆节 |
| &lt;holiday_month&gt; | 10月份 |


_举例：数据部分_
```
    "results": [
        {
            "hint": "10月法定假日信息：国庆节，10月1日至8日放假调休，共8天，与中秋连休。9月30日（星期六）上班。中秋节，10月1日至8日放假调休，共8天，与国庆连休。9月30日（星期六）上班。",
            "data": [
                {
                    "desc": "10月1日至8日放假调休，共8天，与中秋连休。9月30日（星期六）上班。",
                    "festival": "2017-10-1",
                    "name": "国庆节"
                },
                {
                    "desc": "10月1日至8日放假调休，共8天，与国庆连休。9月30日（星期六）上班。",
                    "festival": "2017-10-4",
                    "name": "中秋节"
                }
            ],
            "formatType": "text"
        }
    ]
```


# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| holiday | 要查询的节假日 | 中秋节怎么放假 |
| holiday_month | 要查询的月份 | 10月份有哪些假期 |

# 4.返回字段描述

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| desc | string | 假期详细描述 | 10月1日至8日放假调休，共8天，与国庆连休。9月30日（星期六）上班。 |
| festival | string | 节假日日期 | 2017-10-4 |
| name | string | 节假日名称 | 中秋节 |

