## 2.14 TextNews

---

### 2.1.1 服务说明

> \(**TextNews**\)

### 2.1.2 意图说明

> 该服务主要有10个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetNews**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetNews |   |   | news | params | response\_data | response\_field |   |
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
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
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
> 2 . **GetNews**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetNews |   |   | news | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | category | @sys.entity.news_category |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
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
> 3 . **GetNews**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetNews |   |   | news | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | keyword | @sys.any |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
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
