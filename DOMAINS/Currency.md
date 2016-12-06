## 2.5 Currency

---

### 2.1.1 服务说明

> \(**Currency**\)

### 2.1.2 意图说明

> 该服务主要有4个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetExchangeRate**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetExchangeRate |   |   | exchange_rate | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | fcurrency | @sys.entity.entity_currency |   |
>   | tcurrency | @sys.entity.entity_currency |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"1美元等于多少人民币",
    "semantic":{
        "action":"Exchange",
        "params":{
            "tcurrency":{
                "code":0,
                "norm":"人民币",
                "orgin":"人民币"
            },
            "afcurrency":{
                "code":0,
                "norm":"{\"amount\":\"1\",\"unit\":\"USD\",\"org\":[{\"org_amount\":\"1\",\"org_unit\":\"美元\"}]}",
                "orgin":"1美元"
            }
        },
        "service":"Currency"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "toName":"人民币",
            "fromName":"美元",
            "toAmount":"6.88",
            "toCode":"CNY",
            "fromCode":"USD",
            "fromAmount":"1"
        },
        "hint":"1美元等于6.88人民币"
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
> 2 . **Exchange**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | Exchange |   |   | exchange | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | afcurrency | @sys.unit_currency |   |
>   | tcurrency | @sys.entity.entity_currency |   |
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
