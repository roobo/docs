* [Overview](#Overview)
* [URLs](#URLs)
* [/v1/entities/query](#/v1/entities/query)

### Overview {#Overview}

---

创建、获取、更新、删除实体or实体项

### URLs {#URLs}

---

| Method | Definition |
| :--- | :--- |
| POST /v1/entities/query | 获取指定实体的所有实体项 |
| POST /v1/entities/put | 创建or更新实体 |
| POST /v1/entities/put/delete | 删除指定实体 |
| POST /v1/entities/entries/delete | 给指定实体删除一个实体项列表 |

### /v1/entities/query {#/v1/entities/query}

---
_Sample Request_
```
{
    "token":"xx",
    "agentId":"yy",
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
    "name":"abc",
    "entries": [
         {
            "value":"12",
            "synonyms": [
                "12",
                "33",
                "44",
                "55",
                "66",
                "77",
                "88",
                "99",
                "1090"
            ]
        },
         {
            "value":"22",
            "synonyms": [
                "22"
            ]
        }
    ]
}
```



