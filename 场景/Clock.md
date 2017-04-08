## Clock

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [SetClock](#1SetClock)
 * [GetClock](#2GetClock)
 * [DeleteClock](#3DeleteClock)
 * [Delay](#4Delay)
 * [SetClock](#5SetClock)
 * [DeleteClock](#6DeleteClock)
 * [Stop](#7Stop)
 * [SetClock](#8SetClock)
 * [DeleteClock](#9DeleteClock)

### 服务说明 {#服务说明}

---

\(**Clock**\)

### 意图说明 {#意图说明}

---

该服务主要有9个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| SetClock |  |  | clock |
| GetClock |  |  |  |
| DeleteClock |  |  |  |
| Delay |  |  |  |
| SetClock |  |  |  |
| DeleteClock |  |  | del_clock |
| Stop |  |  |  |
| SetClock |  | clock |  |
| DeleteClock |  | del_clock |  ||

#### SetClock {#1SetClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| alarm_repeat | @sys.entity.alarm_repeat |  |
| content | @sys.any |  |
| date | @sys.date |  |
| date_repeat | @sys.date_repeat |  |
| time_period | @sys.entity.time_period |  ||

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
    "query":"明天上午十点叫我",
    "semantic":{
        "action":"SetClock",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-09",
                "orgin":"明天"
            },
            "date_time":{
                "code":0,
                "norm":"2016-12-08 10:00:00",
                "orgin":"上午十点"
            }
        },
        "service":"Clock"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "content":"",
            "repeat_mode":0,
            "alarm_time":"2016-12-09 10:00:00"
        },
        "hint":"好的主人，已为您设定2016-12-09 10:00的闹钟"
    }
}

```

#### GetClock {#2GetClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| date_time | @sys.date_time |  |
| direction | @sys.entity.direction |  |
| time | @sys.time |  |
| time_period | @sys.entity.time_period |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### DeleteClock {#3DeleteClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| alarm_repeat | @sys.entity.alarm_repeat |  |
| date | @sys.date |  |
| date_repeat | @sys.date_repeat |  |
| date_time | @sys.date_time |  |
| direction | @sys.entity.direction |  |
| time | @sys.time |  |
| time_period | @sys.entity.time_period |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Delay {#4Delay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| time | @sys.time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### SetClock {#5SetClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| alarm_repeat | @sys.entity.alarm_repeat |  |
| content | @sys.any |  |
| date | @sys.date |  |
| date_repeat | @sys.date_repeat |  |
| date_time | @sys.date_time |  |
| time | @sys.time |  ||

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
    "query":"明天上午十点叫我",
    "semantic":{
        "action":"SetClock",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-09",
                "orgin":"明天"
            },
            "date_time":{
                "code":0,
                "norm":"2016-12-08 10:00:00",
                "orgin":"上午十点"
            }
        },
        "service":"Clock"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "content":"",
            "repeat_mode":0,
            "alarm_time":"2016-12-09 10:00:00"
        },
        "hint":"好的主人，已为您设定2016-12-09 10:00的闹钟"
    }
}

```

#### DeleteClock {#6DeleteClock}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Stop {#7Stop}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### SetClock {#8SetClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| date_time | @sys.date_time |  |
| time | @sys.time |  ||

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
    "query":"明天上午十点叫我",
    "semantic":{
        "action":"SetClock",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-09",
                "orgin":"明天"
            },
            "date_time":{
                "code":0,
                "norm":"2016-12-08 10:00:00",
                "orgin":"上午十点"
            }
        },
        "service":"Clock"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "content":"",
            "repeat_mode":0,
            "alarm_time":"2016-12-09 10:00:00"
        },
        "hint":"好的主人，已为您设定2016-12-09 10:00的闹钟"
    }
}

```

#### DeleteClock {#9DeleteClock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| alarm_repeat | @sys.entity.alarm_repeat |  |
| date | @sys.date |  |
| date_repeat | @sys.date_repeat |  |
| date_time | @sys.date_time |  |
| direction | @sys.entity.direction |  |
| num | @sys.number |  |
| time | @sys.time |  |
| time_period | @sys.entity.time_period |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


