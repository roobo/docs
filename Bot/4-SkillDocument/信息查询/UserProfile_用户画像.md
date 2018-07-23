# 1. 服务简介

用户可以设置和查询自己的画像信息。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| prop | 画像属性 | 生日、名字、电话 |
| rel | 画像关系 | 爸爸、哥哥、朋友 |
| told | 画像属性值，Record意图中使用 | 小明（名字）、2014年6月（生日） |


# 3.意图

## Record
记录画像属性
<br>Example:
<br>请记住我的电话是123456789?
<br>请记住我的好朋友的名字是小明?

### request
```
request:
{
    "query":"请记住我的名字叫小明",
    "sessionId": "xxxxxx",
    "agentId":"xxxxxx",
    "token":"xxxxxxxx"
}
```
### response
```
"results": [
  {
    "hint": "好的，我记住了",
    "outputSpeech": {
      "items": [
        {
          "type": "PlainText",
          "source": "好的，我记住了"
        }
      ]
    }
  }
]
```

## Search
查询画像属性
<br>Example:
<br>我的电话是多少?
<br>我的好朋友的名字是什么?

### request
```
request:
{
    "query":"我的好朋友的名字是什么",
    "sessionId": "xxxxxx",
    "agentId":"xxxxxx",
    "token":"xxxxxxxx"
}
```

### response
```
"results": [
  {
    "hint": "小明",
    "outputSpeech": {
      "items": [
        {
          "type": "PlainText",
          "source": "小明"
        }
      ]
    }
  }
]
```
