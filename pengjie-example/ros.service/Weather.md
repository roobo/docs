## 2.1 Weather

---

### 2.1.1 服务说明

> (**Weather**)

### 2.1.2 意图说明

> 该服务主要有8个意图(**Action**)，相应的功能、名称介绍如下。
> 
> 1.**PollutionADay**
> 
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | PollutionADay |   |   | weather | params | response_data | response_field |   |
>
>
> * **参数(params)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | peri | @sys.entity.time_period |   |
>   | city | @sys.entity.city |   |
>   | date | @sys.date |   |
>   | time | @sys.date_time |   |
>
> * **返回数据(response_data)描述**
> ```
>
> ```
>
> * **返回字段(response_field)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
> 2.**WeatherForADay**
> 
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | WeatherForADay |   |   | weather | params | response_data | response_field |   |
>
>
> * **参数(params)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | peri | @sys.entity.time_period |   |
>   | time | @sys.date_time |   |
>   | city | @sys.entity.city |   |
>   | date | @sys.date |   |
>
> * **返回数据(response_data)描述**
> ```
>
> ```
>
> * **返回字段(response_field)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
> 3.**WeatherForDays**
> 
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | WeatherForDays |   |   | weather | params | response_data | response_field |   |
>
>
> * **参数(params)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | duration | @sys.date_duration |   |
>   | city | @sys.entity.city |   |
>
> * **返回数据(response_data)描述**
> ```
>
> ```
>
> * **返回字段(response_field)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
> 4.**PollutionForDays**
> 
>   | 名称 | 功能 | 上文 | 下文 | 参数 | 返回数据 | 返回字段 | 输入样例 |
>   | --- | --- | --- | --- | --- | --- | --- | --- |
>   | PollutionForDays |   |   | weather | params | response_data | response_field |   |
>
>
> * **参数(params)描述**
>
>   | 参数名称 | 参数类型 | 参数描述 |
>   | --- | --- | --- |
>   | duration | @sys.date_duration |   |
>   | city | @sys.entity.city |   |
>
> * **返回数据(response_data)描述**
> ```
>
> ```
>
> * **返回字段(response_field)描述**
>
>   | 字段名称 | 字段描述 |
>   | --- | --- |
>   |  |  |
