## Star

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [Horoscope](#1Horoscope)
 * [Match](#2Match)

### 服务说明 {#服务说明}

---

\(**Star**\)

### 意图说明 {#意图说明}

---

该服务主要有2个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| Horoscope |  |  |  |
| Match |  |  |  ||

#### Horoscope {#1Horoscope}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| constellation | @sys.entity.star_sign |  |
| date | @sys.entity.star_date |  ||

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
    "query":"白羊座今天运势",
    "semantic":{
        "action":"Horoscope",
        "params":{
            "date":{
                "code":0,
                "norm":"今天",
                "orgin":"今天"
            },
            "constellation":{
                "code":0,
                "norm":"白羊座",
                "orgin":"白羊座"
            }
        },
        "service":"Star"
    },
    "result":{
        "formatType":"text",
        "data":{
            "content":""
        },
        "hint":"整体运势：一大早给自己来一顿丰富的早餐，唤醒体内能量，办事效率自然提高。在一些活动聚会有机会结识到不同领域的新朋友，不妨多聊聊，也许日后对你有帮助。消费支出有点高，要控制好自己的物欲。爱情运势：在对方满满的爱意中生活，日子很开心。事业学业：工作压力减轻了许多，态度更加积极向上。财富运势：财政状况不稳定，不适合做大买卖。健康运势：会有肠胃不适的症状发生。"
    }
}

```

#### Match {#2Match}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| constellation1 | @sys.entity.star_sign |  |
| constellation2 | @sys.entity.star_sign |  |
| gender1 | @sys.entity.gender |  |
| gender2 | @sys.entity.gender |  |
| not | @sys.entity.confirm |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


