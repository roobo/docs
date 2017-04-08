## Calculator

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [Calc](#1Calc)
 * [Reciprocal](#2Reciprocal)
 * [Exponent](#3Exponent)
 * [Sqrt](#4Sqrt)
 * [CalcNext](#5CalcNext)

### 服务说明 {#服务说明}

---

\(**Calculator**\)

### 意图说明 {#意图说明}

---

该服务主要有5个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| Calc |  |  | calc_next |
| Reciprocal |  |  |  |
| Exponent |  |  |  |
| Sqrt |  |  |  |
| CalcNext |  | calc_next | calc_next |

#### Calc {#1Calc}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| compute | @sys.compute |  ||

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
    "query":"1加1等于几",
    "semantic":{
        "action":"Calc",
        "params":{
            "compute":{
                "code":0,
                "norm":"(1)+(1)=2",
                "orgin":"1加1"
            }
        },
        "service":"Calculator"
    },
    "result":{
        "formatType":"prop",
        "data":{
            "result":"2",
            "arithmetic":"(1)+(1)"
        },
        "hint":"等于2"
    }
}

```

#### Reciprocal {#2Reciprocal}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| number | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Exponent {#3Exponent}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| expname | @sys.entity.calc_exponent |  |
| expnum | @sys.number |  |
| number | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Sqrt {#4Sqrt}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| number | @sys.number |  |
| sqrtname | @sys.entity.calc_sqrtname |  |
| sqrtnum | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### CalcNext {#5CalcNext}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| formula | @sys.entity.calc_arithmetic |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


