## Video

```
视频点播
```
* [Play](#Play)
* [GetMarket](#2GetMarket)
* [GetStock](#3GetStock)
* [GetStock](#4GetStock)



#### Video: Play {#Play}

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

