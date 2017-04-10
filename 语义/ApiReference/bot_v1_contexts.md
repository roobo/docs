### /bot/v1/contexts

* [Overview](#Overview)
* [URLs](#URLs)
* [POST /v1/contexts/set](#contextssapi1)
* [POST /v1/contexts/delete](#contextssapi2)

### Overview {#Overview}

---

设置or删除上下文。

### URLs {#URLs}

---

| Method | Definition |
| :--- | :--- |
| POST /bot/v1/contexts/set | 设置上下文 |
| POST /bot/v1/contexts/delete | 删除上下文 |

### /bot/v1/contexts/set {#contextssapi1}

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

### /bot/v1/contexts/delete {#contextssapi2}

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



