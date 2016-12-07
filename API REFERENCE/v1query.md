### /v1/query

* [Overview](#Overview)
* [URLs](#URLs)
* [Query Parameters and JSON Fields](#query_1)
* [POST /v1/query](#query_2)

### Overview {#Overview}

---

对输入的自然语言文本进行意图识别，返回意图名称及其参数。

### URLs {#URLs}

---

| Method | Definition |
| :--- | :--- |
| POST /v1/query | 接收返回均使用JSON表示 |

### Query Parameters and JSON Fields {#query_1}

---

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| query | String | 文本自然语言 \(&lt;=255 char\) | Required |
| sessionId | String | 用于区分client并为其管理上下文信息 \(&lt;=128 char\) | Required |
| agentId | String | 应用唯一凭证 \(&lt;=64 char\) | Required |
| token | String | 访问凭证 \(&lt;=64 char\) | Required |
| contexts | String | Context对象数组，若client输入上文，替换server上文 | Optional |
| location | String | Location对象，可以包含经纬度以及详细地址 | Optional |

### /v1/query {#query_2}

---

_Sample Request_

```
{
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "id":219
}
```

_Sample Response_

```
{
    "status": {
        "code":0,
        "errorType":"success"
    },
    "id":219,
    "name":"city",
    "entries": [
         {
            "value":"北京市",
            "synonyms": [
                "北京市",
                "北京",
                "北平市",
                "北平"
            ]
        },
        {
            "value":"西安市",
            "synonyms": [
                "西安市",
                "西安"
            ]
        }
    ]
}
```

### /v1/entities/put {#entitiesapi_2}

---

_Sample Request_

```
{
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "name":"city",
    "entries": [
         {
            "value":"北京",
            "synonyms": [
                "北京市",
                "北京",
                "北平市",
                "北平"
            ]
        },
         {
            "value":"西安市",
            "synonyms": [
                "西安市",
                "西安",
                "长安"
            ]
        }
    ]
}
```

_Sample Response_

```
{
    "status": {
        "code":0,
        "errorType":"success"
    },
    "id":219
}
```

### /v1/entities/delete {#entitiesapi_3}

---

_Sample Request_

```
{
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "id":219 
}
```

_Sample Response_

```
{
    "status": {
        "code":0,
        "errorType":"success"
    }
}
```

### /v1/entities/entries/delete {#entitiesapi_4}

---

_Sample Request_

```
{
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "id":219 
}
{
    "token":"f7caaf310da3dcb24bacdc7944456210",
    "agentId":"2ZmNzYyOTA5MzJjZ",
    "id":219,
    "entries": [
        "西安市"
    ]
}
```

_Sample Response_

```
{
    "status": {
        "code":0,
        "errorType":"success"
    }
}
```



