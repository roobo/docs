### Result

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| hint | String | 读出or展示给用户的文本 | Optional |
| data | JSON OBJECT | 服务填充的数据域 | Optional |
| formattype | String | 用来表示如何对data数据进行读和展示 | Optional |
| timeout | Timeout Object | 超时 | Optional |

---

* **formattype**

  * _text_

    ```
    此时，data必须包含，且只支持一行。
    系统组织方式为，先读hint，再读data["content"]列，再读hintlast,nextop。

    "result":{
      "hint":"请听笑话",
      "data":{
          "CONTENT":"从前......."
      },
      "formatType":"text"
    }
    ```

  * _audio_

    ```
    此时，data必须包含，且只有一行。
    系统组织方式为，先读hint，再读singer的song，如artist不存在，则读song，再读hintlast,nextop,除了audio，其它字段都可能不存在。

    "result":{
      "hint":"为您播放",
      "data":{
          "image":"http://www.XXXX",
          "audio":"http://www.XXXX",
          "album":"专辑名",
          "artist":"歌手名",
          "name":"歌名"
      },
      "formatType":"audio"
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
      "formatType":"list"
    }
    ```

---

* **timeout**

```
"timeout":{
    "timeInMs": 5000,
    "action": "get"
}
```

---



