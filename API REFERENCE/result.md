### Result {#result_1}

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| hint | String | 读出or展示给用户的文本 | Optional |
| data | JSON OBJECT | 服务填充的数据域 | Optional |
| formattype | String | 用来表示如何对data数据进行读和展示 | Optional |
| formatspeak | String | 定义每行数据念的方式 | Optional |
| formatshow | String | 定义数据展示的方式 | Optional |
| hitlast | String | 提示语 | Optional |
| nextop | \[\]String | 引导 | Optional |

---

* **formattype**

    * _text_

      ```
此时，data必须包含，且只支持一行，系统组织方式为，先读hint，再读data["content"]列，再读hintlast,nextop。

    "result":{
        "hint":"请听笑话",
        "data":{
            "content":"从前......."
        },
        "formatType":"text",
        "nextop":[
            "再来一个",
            "不好玩"
        ]
    }
      ```

    * _image_

    * _video_

    * _audio_

    * _abstract_

    * _prop_

    * _list_


