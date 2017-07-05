### /bot/v1/entities
* [概述]
* [URLs]
* [POST /bot/v1/entities/query]
* [POST /bot/v1/entities/put]
* [POST /bot/v1/entities/delete]
* [POST /bot/v1/entities/entries/delete]

### 1 概述
 
---

获取、创建、更新、删除 实体or实体项。

### 2 URLs

---

| Method | Definition |
| :--- | :--- |
| POST /bot/v1/entities/query | 获取指定实体的所有实体项 |
| POST /bot/v1/entities/put | 创建or更新实体 |
| POST /bot/v1/entities/delete | 删除指定实体 |
| POST /bot/v1/entities/entries/delete | 给指定实体删除一个实体项列表 |

### 3 /bot/v1/entities/query

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

### 4 /bot/v1/entities/put

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

### 5 /bot/v1/entities/delete

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

### 6 /bot/v1/entities/entries/delete

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

