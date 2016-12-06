## 2.10 Poetry

---

### 2.1.1 服务说明

> \(**Poetry**\)

### 2.1.2 意图说明

> 该服务主要有28个意图\(**Action**\)，相应的功能、名称介绍如下。
>
>
> 1 . **GetMoreTitles**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetMoreTitles |   |   | poetry,get_moretitles | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | author | @sys.entity.poetry_author |   |
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
> 2 . **GetPhrase**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetPhrase |   |   | poetry,get_phrase | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | classic | @sys.entity.poetry_classic |   |
>   | content | @sys.entity.poetry_content |   |
>   | verse | @sys.any |   |
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
> 3 . **GetAuthorName**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetAuthorName |   |   | poetry,get_author | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | classic | @sys.entity.poetry_classic |   |
>   | content | @sys.entity.poetry_content |   |
>   | title | @sys.entity.poetry_title |   |
>   | verse | @sys.any |   |
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
> 4 . **GetNextPhrase**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetNextPhrase |   |   | poetry,get_nextphrase | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | classic | @sys.entity.poetry_classic |   |
>   | content | @sys.entity.poetry_content |   |
>   | verse | @sys.any |   |
>
>  * **返回数据\(response\_data\)描述**
>
>  * ```go
>    {
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"黄河入海流的下一句",
    "semantic":{
        "action":"GetNextPhrase",
        "params":{
            "verse":{
                "code":0,
                "norm":"[{\"content\":\"黄河入海流\"}]",
                "orgin":"[{\"content\":\"黄河入海流\"}]"
            }
        },
        "service":"Poetry"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "verse":"欲穷千里目",
            "title":"登鹳雀楼",
            "author":"王之涣"
        },
        "hint":"欲穷千里目"
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
> 5 . **GetLastPhrase**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetLastPhrase |   |   | poetry,get_lastphrase | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | classic | @sys.entity.poetry_classic |   |
>   | content | @sys.entity.poetry_content |   |
>   | verse | @sys.any |   |
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
> 6 . **GetTitle**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetTitle |   |   | poetry,get_title | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | classic | @sys.entity.poetry_classic |   |
>   | content | @sys.entity.poetry_content |   |
>   | verse | @sys.any |   |
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
> 7 . **GetAuthorProfile**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetAuthorProfile |   |   | poetry,get_author_profile | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | author | @sys.entity.poetry_author |   |
>   | title | @sys.entity.poetry_title |   |
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
> 8 . **GetTranslation**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetTranslation |   |   | poetry,get_translation | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | title | @sys.entity.poetry_title |   |
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
> 9 . **GetPoetryByTitle**
>
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | GetPoetryByTitle |   |   |  | params | response\_data | response\_field |   |
>
>
>  * **参数\(params\)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | title | @sys.entity.poetry_title |   |
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
