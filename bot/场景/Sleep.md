## Sleep

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [SetSleep](#1SetSleep)

### 服务说明 {#服务说明}

---

\(**Sleep**\)

### 意图说明 {#意图说明}

---

该服务主要有1个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| SetSleep |  |  |  ||

#### SetSleep {#1SetSleep}

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
    "query":"休息吧",
    "semantic":{
        "action":"SetSleep",
        "service":"Sleep"
    }
}

```

