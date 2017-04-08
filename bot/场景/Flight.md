## Flight

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetFlights](#1GetFlights)
 * [GetMore](#2GetMore)
 * [Cancel](#3Cancel)
 * [ChooseFlight](#4ChooseFlight)
 * [GetFlights](#5GetFlights)
 * [CheckCommit](#6CheckCommit)
 * [Default](#7Default)

### 服务说明 {#服务说明}

---

\(**Flight**\)

### 意图说明 {#意图说明}

---

该服务主要有7个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetFlights |  |  | flight |
| GetMore |  | flight | flight |
| Cancel |  | flight |  |
| ChooseFlight |  | flight | flight |
| GetFlights |  | flight | flight |
| CheckCommit |  | flight | flight |
| Default |  | flight | flight |

#### GetFlights {#1GetFlights}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| beginTime | @sys.time |  |
| DepartDate | @sys.date |  |
| DestCity | @sys.entity.city |  |
| highPrice | @sys.number |  |
| priceAver | @sys.number |  |
| StartCity | @sys.entity.city |  |
| timeAver | @sys.time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorDetails":"get roobo answer failed",
        "errorType":"not_supported",
        "code":501
    }
}

```

#### GetMore {#2GetMore}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Cancel {#3Cancel}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ChooseFlight {#4ChooseFlight}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| readID | @sys.ordinal |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetFlights {#5GetFlights}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| beginTime | @sys.time |  |
| DepartDate | @sys.date |  |
| DestCity | @sys.entity.city |  |
| highPrice | @sys.number |  |
| priceAver | @sys.number |  |
| StartCity | @sys.entity.city |  |
| timeAver | @sys.time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorDetails":"get roobo answer failed",
        "errorType":"not_supported",
        "code":501
    }
}

```

#### CheckCommit {#6CheckCommit}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| committag | @sys.entity.confirm |  |
| DepartDate | @sys.date |  |
| UnknownDate | @sys.date |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Default {#7Default}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| defaultVal | @sys.any |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


