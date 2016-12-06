## 2.7 Food

---

### 2.1.1 服务说明

> \(**Food**\)

### 2.1.2 意图说明

> 该服务主要有5个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetFood**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetFood |   |   | food,food_location | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | category | @sys.entity.food_category |   |
>   | inputLocation | @sys.any |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"附近有什么好吃的地方",
    "semantic":{
        "service":"Chat"
    },
    "result":{
        "data":{
            "emotion":[
                {
                    "score":"",
                    "type":"text_question",
                    "value":"normal"
                },
                {
                    "score":"",
                    "type":"text_answer",
                    "value":"normal"
                }
            ]
        },
        "hint":"万塘路有一些吃的，弄堂里是一个"
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
