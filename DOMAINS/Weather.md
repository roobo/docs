## 2.19 Weather

---

### 2.1.1 服务说明

> \(**Weather**\)

### 2.1.2 意图说明

> 该服务主要有8个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **PollutionADay**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | PollutionADay |   |   | weather | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | city | @sys.entity.city |   |
>   | date | @sys.date |   |
>   | peri | @sys.entity.time_period |   |
>   | time | @sys.date_time |   |
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
> 2 . **WeatherForADay**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | WeatherForADay |   |   | weather | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | city | @sys.entity.city |   |
>   | date | @sys.date |   |
>   | peri | @sys.entity.time_period |   |
>   | time | @sys.date_time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"北京今天天气",
    "semantic":{
        "action":"WeatherForADay",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-06",
                "orgin":"今天"
            },
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"Weather"
    },
    "result":{
        "formatType":"list",
        "data":[
            {
                "city":"北京",
                "maxTemp":"6",
                "temperature":"-6",
                "index":1,
                "minTemp":"-3",
                "weather":"多云",
                "date":"2016-12-06",
                "pm25":"59"
            }
        ],
        "hint":"北京 今天多云,零下3度到6度,和昨天差不多,咦，好多好多云彩。"
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
> 3 . **WeatherForDays**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | WeatherForDays |   |   | weather | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | city | @sys.entity.city |   |
>   | duration | @sys.date_duration |   |
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
> 4 . **PollutionForDays**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | PollutionForDays |   |   | weather | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | city | @sys.entity.city |   |
>   | duration | @sys.date_duration |   |
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
