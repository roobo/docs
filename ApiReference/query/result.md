### Result

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| hint | String | 读出or展示给用户的文本 | Optional |
| data | JSON OBJECT | 服务填充的数据域 | Optional |
| formattype | String | 消息类型 | Optional |
| timeout | Timeout Object | 超时 | Optional |

---

* **formattype**

  * _text_

    ```
    "result":{
      "hint":"请听笑话",
      "data":{
          "CONTENT":"从前......."
      },
      "formatType":"text"
    }
    ```

  * _music_

    ```
    "result":{
      "hint":"请欣赏刘德华的忘情水",
      "data":{
          "TITLE":"忘情水",
          "DESCRIPTION":"刘德华",
          "URL":"http://"
      },
      "formatType":"music"
    }
    ```


* **timeout**

```
"timeout":{
    "timeInMs": 5000,
    "action": "get"
}
```

---



