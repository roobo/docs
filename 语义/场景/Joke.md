## Joke

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetJoke](#1GetJoke)
 * [GetJoke](#2GetJoke)

### 服务说明 {#服务说明}

---

\(**Joke**\)

### 意图说明 {#意图说明}

---

该服务主要有2个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetJoke |  |  | joke |
| GetJoke |  | joke | joke |

#### GetJoke {#1GetJoke}

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| joke_tag | @sys.entity.joke_tag |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"讲个笑话",
    "semantic":{
        "action":"GetJoke",
        "service":"Joke"
    },
    "result":{
        "formatType":"text",
        "data":{
            "content":""
        },
        "hint":"木对杉说：你什么时侯身上被砍了三刀？现在的人太不注意保护我们树木了。"
    }
}

```

#### GetJoke {#2GetJoke}

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

```go
{
    "status":{
        "errorType":"success",
        "code":0
    },
    "query":"讲个笑话",
    "semantic":{
        "action":"GetJoke",
        "service":"Joke"
    },
    "result":{
        "formatType":"text",
        "data":{
            "content":""
        },
        "hint":"一哥们儿鼓起勇气在QQ上向MM深情表白。一会儿MM回复：“我是她的妈妈，我是来偷菜的。”"
    }
}

```

