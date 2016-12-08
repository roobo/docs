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
此时，data必须包含，且只支持一行。
系统组织方式为，先读hint，再读data["content"]列，再读hintlast,nextop。

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

      ```
此时，data必须包含，且只支持一行。
系统组织方式为，先读hint，
再读hintlast,nextop,中间展示图片data["image"]。

    "result":{
        "hint":"找到图片",
        "data":{
            "image":"http://www.XXXX"
        },
        "formatType":"image",
        "nextop":[
            "再来一个",
            "太差了"
        ]
    }

      ```

    * _video_

    ```
此时，data必须包含，且只有一行。
系统组织方式为，先读hint，再读data["title"]，再读hintlast,nextop。

    "result":{
        "hint":"为您推荐",
        "data":{
            "video":"http://www.XXXX",
            "title":"美国队长"
        },
        "formatType":"video",
        "nextop":[
            "再来一个",
            "太差了"
        ]
    }

    ```

    * _audio_

    ```
此时，data必须包含，且只有一行。
系统组织方式为，先读hint，再读singer的song，如singer不存在，则读song，再读hintlast,nextop,除了audio，其它字段都可能不存在。

    "result":{
        "hint":"为您播放",
        "data":{
            "image":"http://www.XXXX",
            "audio":"http://www.XXXX",
            "album":"专辑名",
            "artist":"歌手名",
            "name":"歌名"
        },
        "formatType":"audio",
        "nextop":[
            "再来一个",
            "太差了"
        ]
    }

    ```

    * _abstract_

    ```
此时，data必须包含，且只有一行。
系统组织方式为，先读hint，再读data["title"]，再读data["abstract"]，再读hintlast,nextop。

    "result":{
        "hint":"为您推荐",
        "data":{
            "image":"http://www.XXXX",
            "title":"标题",
            "abstract":"摘要"
        },
        "formatType":"abstract",
        "nextop":[
            "再来一个",
            "太差了"
        ]
    }

    ```

    * _prop_

    ```
此时，data必须包含，且只有一行。
系统组织方式为，先读hint，再根据formatspeak读，data["image"]表示展示图,data["url"]表示对应链接，再读hintlast,nextop。

    "result":{
        "hint":"xxxxxx",
        "data":{
            "image":"http://www.XXXX",
            "url":"http://.....",
            "xxx1":"xxxxx",
            "xxx2":"xxxxx"
        },
        "formatType":"prop",
        "formatSpeak":"${xxx1}有一架${xxx2}的航班，价格是${xxx3}元",
        "formatShow":"序号_${index}|航班号_${flightNo}|出发地_${from}|目的地_${to}|时间_${time}|价格_${price}",
        "hintlast":"xxxx",
        "nextop":[
            "再来一个",
            "太差了"
        ]
    }

    ```

    * _list_

    ```
此时，data必须包含。
系统组织方式为，先读hint，再根据formatspeak读，data["index"]表示第几个,data["image"]表示小图标，可没有，data["url"]表示对应链接，可没有。再读hintlast,nextop。

    "result":{
        "hint":"为您找到以下航班",
        "data":[
            {
                "index":1,
                "image":"http://xxx",
                "url":"http://xxx",
                "flightNo":"HN7865",
                "from":"北京",
                "to":"西安",
                "time":"2016-08-16 09:00:00",
                "price":"1001"
            },
            {
                "index":2,
                "image":"http://xxx",
                "url":"http://xxx",
                "flightNo":"DF3621",
                "from":"北京",
                "to":"西安",
                "time":"2016-08-16 09:50:00",
                "price":"1599"
            }
        ],
        "formatType":"list",
        "formatSpeak":"${time}有一架${flightNo}的航班，价格是${price}元",
        "formatShow":"序号_${index}|航班号_$f{lightNo}|出发地_${from}|目的地_${to}|时间_${time}|价格_${price}",
        "hitLast":"请选择",
        "nextop":[
            "确认",
            "取消"
        ]
    }

    ```

