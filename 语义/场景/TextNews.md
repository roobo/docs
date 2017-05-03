## TextNews

* [服务说明](#服务说明)
* [意图说明](#意图说明)
 * [GetNews](#1GetNews)
 * [GetNews](#2GetNews)
 * [GetNews](#3GetNews)
 * [GetNews](#4GetNews)
 * [Break](#5Break)
 * [GetOneNews](#6GetOneNews)
 * [GetOneNews](#7GetOneNews)
 * [Stop](#8Stop)
 * [Pause](#9Pause)
 * [Resume](#10Resume)

### 服务说明

---

文本新闻

### 意图说明

---

该服务主要有10个意图\(**Action**\)，相应的功能、名称介绍如下。

| 名称 | 功能 | 上文 | 下文 |
| :---: | :---: | :---: | :---: |
| GetNews |  |  | news |
| GetNews |  |  | news |
| GetNews |  |  | news |
| GetNews |  | news | news |
| Break |  | news | news |
| GetOneNews |  | news | news |
| GetOneNews |  | news | news |
| Stop |  | news |  |
| Pause |  | news | news |
| Resume |  | news | news |

#### GetNews

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
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
    }
}

```

#### GetNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| category | @sys.entity.news_category |  ||

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
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
    }
}

```

#### GetNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| keyword | @sys.any |  ||

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
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
    }
}

```

#### GetNews

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
    "query":"这两天有关于娱乐的新闻",
    "semantic":{
        "action":"GetNews",
        "params":{
            "keyword":{
                "code":0,
                "norm":"娱乐",
                "orgin":"娱乐"
            }
        },
        "service":"TextNews"
    },
    "result":{
        "hint":"当前时段没有新的新闻资讯"
    }
}

```

#### Break

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetOneNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| keyword | @sys.any |  |
| num | @sys.number |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### GetOneNews

---

* **参数描述**

| 参数名称 | 参数类型 | 参数描述 |
| :---: | :---: | :---: |
| direction | @sys.entity.direction |  ||

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Stop

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Pause

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


#### Resume

---

* **参数描述**

  \(无\)

* **返回字段描述**

| 字段名称 | 字段描述 |
| :---: | :---: |
|  |  ||

* **返回数据描述**

 \(**无**\)


### 新闻数据说明

---
#### 数据源


文本新闻数据来自今日头条，每10分钟更新一次新闻数据。

#### 基础数据格式


抓取自今日头条的新闻数据格式如下，其中title为新闻标题，url为网页链接地址，time为新闻发表时间，source为新闻来源，tags为新闻分类标签，keywords为新闻涉及到的关键词，content为新闻正文。
```go
{
    "content": "土耳其总统埃尔多安土耳其总统雷杰普·塔伊普·埃尔多安１０月２９日说，土耳其将在与伊拉克交界的锡洛皮镇增派军力，如果伊拉克什叶派民兵对靠近土边境的伊拉克城市泰勒阿费尔动武，土方将给予“不同的回应”。多个伊拉克什叶派民兵组织２９日在极端组织“伊斯兰国”占据的伊北部城市摩苏尔以西开辟一条新战线。民兵组织当天在伊朗军事顾问的指挥下，朝摩苏尔以西５５公里的泰勒阿费尔挺进。泰勒阿费尔是什叶派阿拉伯人和土库曼人聚居区。土耳其政府先前多次警告，如果泰勒阿费尔遭到攻击，土方将采取行动。路透社报道，埃尔多安在２９日举行的土耳其国庆招待会上告诉记者，目前没有消息表明伊拉克什叶派民兵组织将对泰勒阿费尔发起进攻。他没有透露将派出多少增援部队，也没有说明将采取何种“不同的回应”。（郑思远）【新华社微特稿】",
    "keywords": [
    	"中东局势",
	"土库曼斯坦",
	"ISIS",
	"环球军事"
    ],
    "source": "新华网",
    "tags": [
	"热点",
	"国际"
    ],
    "time": "2016-11-01 06:40",
    "title": "埃尔多安：土耳其拟增兵伊拉克边境已警告多次",
    "url": "http://www.toutiao.com/group/6338536719386231042/"
}
```

### RoadMap

---
#### 新闻推荐

实现简单的基于用户浏览记录+关键字的新闻推荐功能。
