## Stock

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetPicture](#1GetPicture)
 * [GetMarket](#2GetMarket)
 * [GetStock](#3GetStock)
 * [GetStock](#4GetStock)

### 服务说明 {#服务说明}

---

\(**Stock**\)

### 意图说明 {#意图说明}

---

该服务主要有4个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetPicture |  |  | stock |
| GetMarket |  |  | stock |
| GetStock |  |  | stock |
| GetStock |  | stock | stock |

#### GetPicture {#1GetPicture}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| picturetype | @sys.entity.stock_picture |  |
| stockid | @sys.entity.stock_code |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetMarket {#2GetMarket}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetStock {#3GetStock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| stockid | @sys.entity.stock_code |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorDetails":"invalid character '<' looking for beginning of value",
        "errorType":"service_unknown_format",
        "code":602
    },
    "query":"长和今天的股价"
}

```

#### GetStock {#4GetStock}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| date | @sys.date |  |
| stockid | @sys.entity.stock_code |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorDetails":"invalid character '<' looking for beginning of value",
        "errorType":"service_unknown_format",
        "code":602
    },
    "query":"长和今天的股价"
}

```

