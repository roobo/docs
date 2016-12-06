## 2.8 Joke

---

### 2.1.1 服务说明

> \(**Joke**\)

### 2.1.2 意图说明

> 该服务主要有2个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetJoke**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetJoke |   |   | joke | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | joke_tag | @sys.entity.joke_tag |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"讲个笑话",
    "semantic":{
        "action":"GetJoke",
        "service":"Joke"
    },
    "result":{
        "formatType":"text",
        "data":{
            "content":""
        },
        "hint":"上次我表姐带着儿子去动物园，表姐的儿子和猴子叽咕一阵，猴子跑回去拿了根香蕉塞到小孩子手里……猴子的母性是不是特别重啊？"
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
