## TextNews

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetNews](#1GetNews)
 * [GetNews](#2GetNews)
 * [GetNews](#3GetNews)
 * [GetNews](#4GetNews)
 * [Break](#5Break)
 * [GetOneNews](#6GetOneNews)
 * [GetOneNews](#7GetOneNews)
 * [Stop](#8Stop)
 * [Pause](#9Pause)
 * [Resume](#10Resume)

### 服务说明

---

文本新闻

### 意图说明

---

该服务主要有10个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetNews |  |  | news |
| GetNews |  |  | news |
| GetNews |  |  | news |
| GetNews |  | news | news |
| Break |  | news | news |
| GetOneNews |  | news | news |
| GetOneNews |  | news | news |
| Stop |  | news |  |
| Pause |  | news | news |
| Resume |  | news | news |

#### GetNews

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

```

#### GetNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| category | @sys.entity.news_category |  ||

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

```

#### GetNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| keyword | @sys.any |  ||

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

```

#### GetNews

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

```

#### Break

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetOneNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| keyword | @sys.any |  |
| num | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetOneNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| direction | @sys.entity.direction |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Stop

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Pause

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


