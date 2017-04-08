## Weather

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [PollutionADay](#1PollutionADay)
 * [WeatherForADay](#2WeatherForADay)
 * [WeatherForDays](#3WeatherForDays)
 * [PollutionForDays](#4PollutionForDays)
 * [PollutionADay](#5PollutionADay)
 * [WeatherForADay](#6WeatherForADay)
 * [WeatherForDays](#7WeatherForDays)
 * [WeatherForADay](#8WeatherForADay)

### 服务说明 {#服务说明}

---

\(**Weather**\)

### 意图说明 {#意图说明}

---

该服务主要有8个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| PollutionADay |  |  | weather |
| WeatherForADay |  |  | weather |
| WeatherForDays |  |  | weather |
| PollutionForDays |  |  | weather |
| PollutionADay |  | weather | weather |
| WeatherForADay |  | weather | weather |
| WeatherForDays |  | weather | weather |
| WeatherForADay |  | weather_need_city | weather |

#### PollutionADay {#1PollutionADay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| date | @sys.date |  |
| peri | @sys.entity.time_period |  |
| time | @sys.date_time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### WeatherForADay {#2WeatherForADay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| date | @sys.date |  |
| peri | @sys.entity.time_period |  |
| time | @sys.date_time |  ||

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
    "query":"北京今天天气",
    "semantic":{
        "action":"WeatherForADay",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-08",
                "orgin":"今天"
            },
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"Weather"
    },
    "result":{
        "formatType":"list",
        "data":[
            {
                "city":"北京",
                "maxTemp":"7",
                "temperature":"1",
                "index":1,
                "minTemp":"-2",
                "weather":"多云转晴",
                "date":"2016-12-08",
                "pm25":"237"
            }
        ],
        "hint":"北京 今天多云转晴,零下2度到7度,和昨天差不多,太阳晒起来好舒服。"
    }
}

```

#### WeatherForDays {#3WeatherForDays}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| duration | @sys.date_duration |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### PollutionForDays {#4PollutionForDays}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| duration | @sys.date_duration |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### PollutionADay {#5PollutionADay}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### WeatherForADay {#6WeatherForADay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| date | @sys.date |  ||

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
    "query":"北京今天天气",
    "semantic":{
        "action":"WeatherForADay",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-08",
                "orgin":"今天"
            },
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"Weather"
    },
    "result":{
        "formatType":"list",
        "data":[
            {
                "city":"北京",
                "maxTemp":"7",
                "temperature":"1",
                "index":1,
                "minTemp":"-2",
                "weather":"多云转晴",
                "date":"2016-12-08",
                "pm25":"237"
            }
        ],
        "hint":"北京 今天多云转晴,零下2度到7度,和昨天差不多,嘻嘻，太阳出来亮堂堂。"
    }
}

```

#### WeatherForDays {#7WeatherForDays}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  |
| duration | @sys.date_duration |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### WeatherForADay {#8WeatherForADay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.city |  ||

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
    "query":"北京今天天气",
    "semantic":{
        "action":"WeatherForADay",
        "params":{
            "date":{
                "code":0,
                "norm":"2016-12-08",
                "orgin":"今天"
            },
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"Weather"
    },
    "result":{
        "formatType":"list",
        "data":[
            {
                "city":"北京",
                "maxTemp":"7",
                "temperature":"1",
                "index":1,
                "minTemp":"-2",
                "weather":"多云转晴",
                "date":"2016-12-08",
                "pm25":"237"
            }
        ],
        "hint":"北京 今天多云转晴,零下2度到7度,和昨天差不多,太阳晒起来好舒服。"
    }
}

```

