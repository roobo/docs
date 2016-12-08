## Poetry

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetOnePoetry](#1GetOnePoetry)
 * [GetPoetryByTitle](#2GetPoetryByTitle)
 * [GetMoreTitles](#3GetMoreTitles)
 * [GetPhrase](#4GetPhrase)
 * [GetAuthorName](#5GetAuthorName)
 * [GetNextPhrase](#6GetNextPhrase)
 * [GetLastPhrase](#7GetLastPhrase)
 * [GetTitle](#8GetTitle)
 * [GetAuthorProfile](#9GetAuthorProfile)
 * [GetTranslation](#10GetTranslation)
 * [Next](#11Next)
 * [Prev](#12Prev)
 * [Pause](#13Pause)
 * [Resume](#14Resume)
 * [Exit](#15Exit)
 * [GetAuthorName](#16GetAuthorName)
 * [GetAuthorProfile](#17GetAuthorProfile)
 * [GetLastPhrase](#18GetLastPhrase)
 * [GetLastPhrase](#19GetLastPhrase)
 * [GetNextPhrase](#20GetNextPhrase)
 * [GetMoreTitles](#21GetMoreTitles)
 * [GetNextPhrase](#22GetNextPhrase)
 * [GetNextPhrase](#23GetNextPhrase)
 * [GetLastPhrase](#24GetLastPhrase)
 * [GetPhrase](#25GetPhrase)
 * [GetLastPhrase](#26GetLastPhrase)
 * [GetNextPhrase](#27GetNextPhrase)
 * [GetTitle](#28GetTitle)
 * [GetTranslation](#29GetTranslation)
 * [GetMoreTitles](#30GetMoreTitles)
 * [GetTranslation](#31GetTranslation)
 * [GetAuthorProfile](#32GetAuthorProfile)
 * [GetAuthorName](#33GetAuthorName)
 * [GetTitle](#34GetTitle)

### 服务说明 {#服务说明}

---

\(**Poetry**\)

### 意图说明 {#意图说明}

---

该服务主要有34个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetOnePoetry |  |  | audiopoetry |
| GetPoetryByTitle |  |  | audiopoetry |
| GetMoreTitles |  |  | poetry,get_moretitles |
| GetPhrase |  |  | poetry,get_phrase |
| GetAuthorName |  |  | poetry,get_author |
| GetNextPhrase |  |  | poetry,get_nextphrase |
| GetLastPhrase |  |  | poetry,get_lastphrase |
| GetTitle |  |  | poetry,get_title |
| GetAuthorProfile |  |  | poetry,get_author_profile |
| GetTranslation |  |  | poetry,get_translation |
| Next |  | audiopoetry | audiopoetry |
| Prev |  | audiopoetry | audiopoetry |
| Pause |  | audiopoetry | audiopoetry |
| Resume |  | audiopoetry | audiopoetry |
| Exit |  | audiopoetry | audiopoetry |
| GetAuthorName |  | get_author | poetry,get_author |
| GetAuthorProfile |  | get_author_profile | poetry,get_author_profile |
| GetLastPhrase |  | get_lastphrase | get_lastphrase,poetry |
| GetLastPhrase |  | get_lastphrase | poetry,get_lastphrase |
| GetNextPhrase |  | get_lastphrase | poetry,get_nextphrase |
| GetMoreTitles |  | get_moretitles | poetry,get_moretitles |
| GetNextPhrase |  | get_nextphrase | get_nextphrase ,poetry |
| GetNextPhrase |  | get_nextphrase | poetry,get_nextphrase |
| GetLastPhrase |  | get_nextphrase | poetry,get_lastphrase |
| GetPhrase |  | get_phrase | poetry,get_phrase |
| GetLastPhrase |  | get_phrase | poetry,get_lastphrase |
| GetNextPhrase |  | get_phrase | poetry,get_nextphrase |
| GetTitle |  | get_title | poetry ,get_title |
| GetTranslation |  | get_translation | poetry,get_translation |
| GetMoreTitles |  | poetry | poetry |
| GetTranslation |  | poetry | poetry |
| GetAuthorProfile |  | poetry | poetry,get_author_profile |
| GetAuthorName |  | poetry | poetry |
| GetTitle |  | poetry | poetry |

#### GetOnePoetry {#1GetOnePoetry}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  |
| dynasty | @sys.entity.poetry_dynasty |  |
| reader | @sys.entity.media_poetry_reader |  |
| tag | @sys.any |  |
| type | @sys.entity.poetry_type |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetPoetryByTitle {#2GetPoetryByTitle}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  |
| dynasty | @sys.entity.poetry_dynasty |  |
| reader | @sys.entity.media_poetry_reader |  |
| tag | @sys.any |  |
| title | @sys.entity.poetry_title |  |
| type | @sys.entity.poetry_type |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetMoreTitles {#3GetMoreTitles}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetPhrase {#4GetPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorName {#5GetAuthorName}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| title | @sys.entity.poetry_title |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetNextPhrase {#6GetNextPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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

```

#### GetLastPhrase {#7GetLastPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTitle {#8GetTitle}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorProfile {#9GetAuthorProfile}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  |
| title | @sys.entity.poetry_title |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTranslation {#10GetTranslation}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| title | @sys.entity.poetry_title |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Next {#11Next}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Prev {#12Prev}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Pause {#13Pause}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume {#14Resume}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Exit {#15Exit}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorName {#16GetAuthorName}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| title | @sys.entity.poetry_title |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorProfile {#17GetAuthorProfile}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  |
| title | @sys.entity.poetry_title |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetLastPhrase {#18GetLastPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetLastPhrase {#19GetLastPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetNextPhrase {#20GetNextPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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

```

#### GetMoreTitles {#21GetMoreTitles}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| author | @sys.entity.poetry_author |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetNextPhrase {#22GetNextPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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

```

#### GetNextPhrase {#23GetNextPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  |
| verse | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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

```

#### GetLastPhrase {#24GetLastPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetPhrase {#25GetPhrase}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetLastPhrase {#26GetLastPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetNextPhrase {#27GetNextPhrase}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
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

```

#### GetTitle {#28GetTitle}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| classic | @sys.entity.poetry_classic |  |
| content | @sys.entity.poetry_content |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTranslation {#29GetTranslation}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| title | @sys.entity.poetry_title |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetMoreTitles {#30GetMoreTitles}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTranslation {#31GetTranslation}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorProfile {#32GetAuthorProfile}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetAuthorName {#33GetAuthorName}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTitle {#34GetTitle}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


