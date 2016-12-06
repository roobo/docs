## 2.11 Sleep

---

### 2.1.1 服务说明

> \(**Sleep**\)

### 2.1.2 意图说明

> 该服务主要有1个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **SetSleep**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | SetSleep |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"休息吧",
    "semantic":{
        "action":"SetSleep",
        "service":"Sleep"
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
