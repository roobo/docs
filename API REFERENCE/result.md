### Result {#result_1}

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| hint | String | 读出or展示给用户的文本 | Optional |
| data | JSON OBJECT | 服务填充的数据域 | Optional |
| formattype | String | 设置ui类型，包括"text","image","video","audio","abstract","list","prop"。用来表示如何对data数据进行读和展示 | Optional |
| formatspeak | String | ${time}有一架${flightNo}的航班，价格是${price}元。定义每行数据念的方式，用data中的数据替换${var} | Optional |
| formatshow | String | 序号_${index}|航班号_$f{lightNo}|出发地_${from}|目的地_${to}|时间_${time}|价格_${price}。定义数据展示的方式，K_V结构，"|"分割多个kv对，V可以是变量加字，K展示为表头，V展示为每列数据 | Optional |
| hitlast | String | 提示语 | Optional |
| nextop | \[\]String | 引导 | Optional |

---

_Sample Response_

| formattype | example |
| :--- | :--- |
|  |  |



