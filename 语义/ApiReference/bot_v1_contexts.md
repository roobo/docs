### /bot/v1/contexts

* [概述]
* [URLs]
* [POST /v1/contexts/set]
* [POST /v1/contexts/delete]
* [POST /v1/contexts/query]

### 1 概述

---

设置or删除上下文。

### 2 URLs

---

| Method | Definition |
| :--- | :--- |
| POST /bot/v1/contexts/set | 设置上下文 |
| POST /bot/v1/contexts/delete | 删除上下文 |
| POST /bot/v1/contexts/query | 获取最近一次交互的上文 |

### 3 /bot/v1/contexts/set

---

_Sample Request_

```
{
    "sessionId":"sn:1212121343545352352",
    "token":"f7caaf310da3ccb24bacdc7944456210",
    "agentId":"xfdsqfafdafdafef332422",
    "contexts":[
        {
            "context":"translate",
            "service":"Translator"
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
    }
}
```

### 4 /bot/v1/contexts/delete

---

_Sample Request_

```
{
    "sessionId":"sn:1212121343545352352",
    "token":"f7caaf310da3ccb24bacdc7944456210",
    "agentId":"xfdsqfafdafdafef332422"
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


### 5 /bot/v1/contexts/query

---

_Sample Request_

```
{
    "sessionId":"sn:1212121343545352352",
    "token":"f7caaf310da3ccb24bacdc7944456210",
    "agentId":"xfdsqfafdafdafef332422"
}
```

_Sample Response_

```
{
    "status": {
        "code":0,
        "errorType":"success"
    },
    "contexts": [
      {
        "service": "Weather",
        "context": "weather_aday"
      }
    ]
}
```


