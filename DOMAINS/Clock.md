## 2.3 Clock

---

### 2.1.1 服务说明

> \(**Clock**\)

### 2.1.2 意图说明

> 该服务主要有9个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **SetClock**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | SetClock |   |   | clock | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | alarm_repeat | @sys.entity.alarm_repeat |   |
>   | content | @sys.any |   |
>   | date | @sys.date |   |
>   | date_repeat | @sys.date_repeat |   |
>   | time_period | @sys.entity.time_period |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"明天上午十点叫我",
    "semantic":{
        "action":"SetClock",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-07",
                "orgin":"明天"
            },
            "date_time":{
                "code":0,
                "norm":"2016-12-06 10:00:00",
                "orgin":"上午十点"
            }
        },
        "service":"Clock"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "content":"",
            "repeat_mode":0,
            "alarm_time":"2016-12-07 10:00:00"
        },
        "hint":"好的主人，已为您设定2016-12-07 10:00的闹钟"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 2 . **GetClock**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetClock |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | date | @sys.date |   |
>   | date_time | @sys.date_time |   |
>   | direction | @sys.entity.direction |   |
>   | time | @sys.time |   |
>   | time_period | @sys.entity.time_period |   |
>
>  * **返回数据\(response\_data\)描述**
>
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 3 . **DeleteClock**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | DeleteClock |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | alarm_repeat | @sys.entity.alarm_repeat |   |
>   | date | @sys.date |   |
>   | date_repeat | @sys.date_repeat |   |
>   | date_time | @sys.date_time |   |
>   | direction | @sys.entity.direction |   |
>   | time | @sys.time |   |
>   | time_period | @sys.entity.time_period |   |
>
>  * **返回数据\(response\_data\)描述**
>
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 4 . **Delay**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Delay |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | time | @sys.time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 5 . **SetClock**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | SetClock |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | alarm_repeat | @sys.entity.alarm_repeat |   |
>   | content | @sys.any |   |
>   | date | @sys.date |   |
>   | date_repeat | @sys.date_repeat |   |
>   | date_time | @sys.date_time |   |
>   | time | @sys.time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"明天上午十点叫我",
    "semantic":{
        "action":"SetClock",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-07",
                "orgin":"明天"
            },
            "date_time":{
                "code":0,
                "norm":"2016-12-06 10:00:00",
                "orgin":"上午十点"
            }
        },
        "service":"Clock"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "content":"",
            "repeat_mode":0,
            "alarm_time":"2016-12-07 10:00:00"
        },
        "hint":"好的主人，已为您设定2016-12-07 10:00的闹钟"
    }
}
>
>    ```
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 6 . **DeleteClock**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | DeleteClock |   |   | del_clock | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>
>  * **返回数据\(response\_data\)描述**
>
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
> 7 . **Stop**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Stop |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>
>  * **返回数据\(response\_data\)描述**
>
>
>  * **返回字段\(response\_field\)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
>
