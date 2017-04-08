## TimeDates

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetDateFromLunarToSolar](#1GetDateFromLunarToSolar)
 * [GetNowMonth](#2GetNowMonth)
 * [GetWeekDay](#3GetWeekDay)
 * [GetYear](#4GetYear)
 * [GetDate](#5GetDate)
 * [GetTime](#6GetTime)
 * [GetDate](#7GetDate)
 * [GetTime](#8GetTime)
 * [GetWeekDay](#9GetWeekDay)
 * [GetYear](#10GetYear)

### 服务说明 {#服务说明}

---

\(**TimeDates**\)

### 意图说明 {#意图说明}

---

该服务主要有10个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetDateFromLunarToSolar |  |  |  |
| GetNowMonth |  |  |  |
| GetWeekDay |  |  | get_date,get_weekday |
| GetYear |  |  | get_year |
| GetDate |  |  | get_date,get_weekday |
| GetTime |  |  | get_time |
| GetDate |  | get_date | get_date,get_weekday |
| GetTime |  | get_time | get_time |
| GetWeekDay |  | get_weekday | get_date,get_weekday |
| GetYear |  | get_year | get_year |

#### GetDateFromLunarToSolar {#1GetDateFromLunarToSolar}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| any | @sys.any |  |
| anydate | @sys.any |  |
| date | @sys.date |  |
| lunar | @sys.entity.lunar |  |
| weekday | @sys.entity.weekday |  |
| year | @sys.year |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetNowMonth {#2GetNowMonth}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetWeekDay {#3GetWeekDay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| any | @sys.any |  |
| date | @sys.date |  |
| weekday | @sys.entity.weekday |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetYear {#4GetYear}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| number | @sys.number |  |
| year | @sys.year |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetDate {#5GetDate}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| lunar | @sys.entity.lunar |  |
| number | @sys.number |  |
| solarterm | @sys.entity.solarterms |  |
| year | @sys.year |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTime {#6GetTime}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.allcity |  |
| country | @sys.entity.country |  |
| time | @sys.date_time |  |
| timequantum | @sys.entity.time_period |  ||

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
    "query":"北京现在几点了",
    "semantic":{
        "action":"GetTime",
        "params":{
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"TimeDates"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "timezone":"Asia/Shanghai",
            "city":"北京",
            "timestamp":1481198017.0
        },
        "hint":"北京现在是晚上7点53分"
    }
}

```

#### GetDate {#7GetDate}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| lunar | @sys.entity.lunar |  |
| number | @sys.number |  |
| solarterm | @sys.entity.solarterms |  |
| year | @sys.year |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetTime {#8GetTime}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| city | @sys.entity.allcity |  |
| country | @sys.entity.country |  |
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
    "query":"北京现在几点了",
    "semantic":{
        "action":"GetTime",
        "params":{
            "city":{
                "code":0,
                "norm":"北京",
                "orgin":"北京"
            }
        },
        "service":"TimeDates"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "timezone":"Asia/Shanghai",
            "city":"北京",
            "timestamp":1481198017.0
        },
        "hint":"北京现在是晚上7点53分"
    }
}

```

#### GetWeekDay {#9GetWeekDay}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| weekday | @sys.entity.weekday |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetYear {#10GetYear}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| number | @sys.number |  |
| year | @sys.year |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


