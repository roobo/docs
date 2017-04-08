## UnitConversion

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [ConvertLength](#1ConvertLength)
 * [ConvertWeight](#2ConvertWeight)
 * [ConvertArea](#3ConvertArea)
 * [ConvertSpeed](#4ConvertSpeed)
 * [ConvertVolume](#5ConvertVolume)
 * [ConvertTemperature](#6ConvertTemperature)
 * [ConvertMoney](#7ConvertMoney)
 * [ConvertTime](#8ConvertTime)
 * [ConvertArea](#9ConvertArea)
 * [ConvertLength](#10ConvertLength)
 * [ConvertMoney](#11ConvertMoney)
 * [ConvertSpeed](#12ConvertSpeed)
 * [ConvertTemperature](#13ConvertTemperature)
 * [ConvertTime](#14ConvertTime)
 * [ConvertVolume](#15ConvertVolume)
 * [ConvertWeight](#16ConvertWeight)

### 服务说明 {#服务说明}

---

\(**UnitConversion**\)

### 意图说明 {#意图说明}

---

该服务主要有16个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| ConvertLength |  |  | length |
| ConvertWeight |  |  | weight |
| ConvertArea |  |  | area |
| ConvertSpeed |  |  | speed |
| ConvertVolume |  |  | volume |
| ConvertTemperature |  |  | temperature |
| ConvertMoney |  |  | money |
| ConvertTime |  |  | unit_time |
| ConvertArea |  | area | area |
| ConvertLength |  | length | length |
| ConvertMoney |  | money | money |
| ConvertSpeed |  | speed | speed |
| ConvertTemperature |  | temperature | temperature |
| ConvertTime |  | unit_time | unit_time |
| ConvertVolume |  | volume | volume |
| ConvertWeight |  | weight | weight |

#### ConvertLength {#1ConvertLength}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_length |  |
| fromUnit | @sys.entity.unit_entity_length |  |
| toUnit | @sys.entity.unit_entity_length |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertWeight {#2ConvertWeight}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_weight |  |
| fromUnit | @sys.entity.unit_entity_weight |  |
| toUnit | @sys.entity.unit_entity_weight |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertArea {#3ConvertArea}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_area |  |
| fromUnit | @sys.entity.unit_entity_area |  |
| toUnit | @sys.entity.unit_entity_area |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertSpeed {#4ConvertSpeed}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_speed |  |
| fromUnit | @sys.entity.unit_entity_speed |  |
| toUnit | @sys.entity.unit_entity_speed |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertVolume {#5ConvertVolume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_volume |  |
| fromUnit | @sys.entity.unit_entity_volume |  |
| toUnit | @sys.entity.unit_entity_volume |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertTemperature {#6ConvertTemperature}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_temperature |  |
| toUnit | @sys.entity.unit_entity_temperature |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertMoney {#7ConvertMoney}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_money |  |
| toUnit | @sys.entity.unit_entity_money |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertTime {#8ConvertTime}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_time |  |
| toUnit | @sys.entity.unit_entity_time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertArea {#9ConvertArea}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_weight |  |
| toUnit | @sys.entity.unit_entity_area |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertLength {#10ConvertLength}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_length |  |
| toUnit | @sys.entity.unit_entity_length |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertMoney {#11ConvertMoney}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_money |  |
| toUnit | @sys.entity.unit_entity_money |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertSpeed {#12ConvertSpeed}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_speed |  |
| toUnit | @sys.entity.unit_entity_speed |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertTemperature {#13ConvertTemperature}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_temperature |  |
| toUnit | @sys.entity.unit_entity_temperature |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertTime {#14ConvertTime}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| amount | @sys.number |  |
| fromUnit | @sys.entity.unit_entity_time |  |
| toUnit | @sys.entity.unit_entity_time |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertVolume {#15ConvertVolume}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_volume |  |
| toUnit | @sys.entity.unit_entity_volume |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### ConvertWeight {#16ConvertWeight}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| fromNumUnit | @sys.unit_weight |  |
| toUnit | @sys.entity.unit_entity_weight |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


