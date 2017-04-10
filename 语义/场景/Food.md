## Food

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetFood](#1GetFood)
 * [ChooseFood](#2ChooseFood)
 * [GetMore](#3GetMore)
 * [ReGetFood](#4ReGetFood)
 * [GetFood](#5GetFood)

### 服务说明 {#服务说明}

---

\(**Food**\)

### 意图说明 {#意图说明}

---

该服务主要有5个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetFood |  |  | food,food_location |
| ChooseFood |  | food | food |
| GetMore |  | food | food |
| ReGetFood |  | food | food |
| GetFood |  | food_location | food |

#### GetFood {#1GetFood}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| category | @sys.entity.food_category |  |
| inputLocation | @sys.any |  ||

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

```

#### ChooseFood {#2ChooseFood}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| resultNum | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetMore {#3GetMore}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ReGetFood {#4ReGetFood}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| category | @sys.entity.food_category |  |
| shopname | @sys.entity.food_shopname |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetFood {#5GetFood}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| inputLocation | @sys.any |  ||

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

```

