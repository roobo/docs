

# 1.服务背景

根据语义，提供新闻服务。

# 2. 槽位

| Slot\_Key | Description | Main\_Application | Example |
| --- | --- | --- | --- |
| news\_tag\_topic | 新闻主题 | 用于指定新闻主题 | 热门 财经 科技 |
| news\_category | 新闻类别 | 已经播放过摘要，需要再次收听时，需指明 | 摘要 快报 |
| keywords | 用户关键词，用于指定人物，事件，话题，地区等 | 刘德华 余额宝 爆炸 |

# 3.意图

## 3.1 Play\_播放新闻

无脑听新闻意图模板：\[我要\|我想\|\]\[听\|\]\[新闻\|新闻资讯\|资讯\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| | 播段新闻 |
| 无脑听新闻意图模板; | 我想听新闻 |
| 无脑听新闻意图模板+&lt;news\_nosencekey&gt; | 我想听新闻快报 |

## 3.2 CategoryNews\_类别新闻

类别新闻意图模板1：\[最近\|这两天\|这段时间\|近来\|\]有

类别新闻意图模板2：\[类\|方面\|那边\|\]\[的\|\]\[新闻\|新闻资讯\|资讯\|消息\]\[吗\|嘛\|\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 类别新闻意图模板1+&lt;news\_category&gt;+类别新闻意图模板2; | 最近有财经新闻吗 |

## 3.3 KeywordsNews\_关键字新闻

关键字新闻意图模板1：\[最近\|这两天\|这段时间\|近来\|\]有\[关于\|\]

关键字新闻意图模板2：\[类\|方面\|那边\|\]\[的\|\]\[新闻\|新闻资讯\|资讯\|消息\]\[吗\|嘛\|\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 关键字新闻意图模板1+&lt;news\_keywords&gt;+关键字新闻意图模板2; | 最近有刘德华新闻吗 |

## 3.4 Prev\_上一个

上一个新闻意图模板：\[上\|前\]一\[条\|篇\|段\|个\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 上一个新闻意图模板; | 上一段 |

## 3.5 Next\_下一个

下一个新闻意图模板：这\[一\|\]\[个\|篇\|则\|段\]不想听了

| **Support\_Semantic** | **Example** |
| --- | --- |
| 下一个新闻意图模板; | 这段不想听了 |

## 3.6 Exit\_停止播报

停止播报新闻意图模板：\[我\|我们\|\]不\[想\|要\]听了

| **Support\_Semantic** | **Example** |
| --- | --- |
| 停止播报新闻意图模板; | 不想听了 |

## 3.7 Pause\_暂停播报

暂停播报新闻意图模板：先别说话\[等一等\|等一下\|\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 暂停播报新闻意图模板; | 先别说话 |

## 3.8 Resume\_继续播报

继续播报新闻意图模板：\[继续\|接着\]\[讲\|报\|播\|播放\|播报\|放\|读\|来\|说\
| **Support\_Semantic** | **Example** |
| --- | --- |
| 接着播报新闻意图模板; | 接着说 |

## 3.9 ChangeNews\_换一批

换一批新闻意图模板：换一批\[新闻\|新闻资讯\|资讯\|消息\|\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 换一批播报新闻意图模板; | 换一批 |

# 4.返回结果

## 4.1 Play\_播放新闻

返回字段说明

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | string | 提示语 | 让我们一起听听闻 |
| data |  |  |  |  |
|  | audio | string | 新闻播放地址 | http://mp3.tingwen.me/data/upload/mp3/596e2a9d01ae2.mp3 |
|  | tagTopic | string | 新闻主题 | 财经 |
|  | timestamp | int | 新闻产生时间戳 | 1502364363 |
|  | title | string | 新闻标题 | 软银集团和共享办公空间公司WeWork在日本成立合资公司 |
|  | type | string | 数据类型 | audio |
| formatType |  | string | 结果类型 | news |

返回字段
```
    "result": {
        "hint": "让我们一起听听闻",
        "data": {
            "audio": "http://mp3.tingwen.me/data/upload/mp3/598c42c453e5c.mp3",
            "tagTopic": "文娱",
            "timestamp": 1502364363,
            "title": "阿里影业联合优酷，开创影视综艺及艺人经纪新模式",
            "type": "audio"
        },
        "formatType": "news"
    }
```

## 4.4 Prev\_上一个
同上

## 4.5 Next\_下一个
同上

## 4.6 Exit\_停止播报

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 提示语 | "" |

```
    "result": {
        "hint": ""
    }
```

## 4.7 Pause\_暂停播报

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 提示语 | "好的，主人" |

```
    "result": {
        "hint": "好的，主人"
    }
```

## 4.8 Resume\_继续播报
同4.5 Next\_下一个

## 4.9 ChangeNews\_换一批
同上
