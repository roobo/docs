## 2.6 Flight

---

### 2.1.1 服务说明

> \(**Flight**\)

### 2.1.2 意图说明

> 该服务主要有7个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetFlights**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetFlights |   |   | flight | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | beginTime | @sys.time |   |
>   | DepartDate | @sys.date |   |
>   | DestCity | @sys.entity.city |   |
>   | highPrice | @sys.number |   |
>   | priceAver | @sys.number |   |
>   | StartCity | @sys.entity.city |   |
>   | timeAver | @sys.time |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorDetails":"get roobo answer failed",
        "errorType":"not_supported",
        "code":501
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
