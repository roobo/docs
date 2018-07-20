
# 1. 服务简介

当前的诗词Bot产品主要为一问一答的播报功能，但缺少与用户更为丰富和沉浸的互动，诗词问答会以闯关形式通过与用户的更多交互满足需求

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| title | 诗词名 | 静夜思 |
| author | 诗词作者 | 李白 |
| verse | 单句诗词 | 床前明月光 |

# 3.意图

## 3.1 Learn_学

 我要**学**静夜思
 
## 3.2 Read_跟读

我要**跟读**静夜思

## 3.3 Abut_对答

我要**对答**静夜思

## 3.4 Recite_背

我要**背诵**静夜思

## 3.5 Next_下一关

下一关

## 3.6 Prev_上一关

上一关

## 3.7 Repeat_重复

重复学习

## 3.8 Exit_退出

退出

# 4.返回结果

返回结果如下json所示。
语音输出方案在response的result字段里的outputSpeech中，以数组的形式，依次读出。目前支持PlainText格式和ssml格式。

## 4.1 Learn_学

query: 我要学静夜思

response:

```
  "results": [
    {
      "hint": "小朋友，跟我一起来学吧，静夜思，唐代，李白，床前明月光，疑是地上霜，举头望明月，低头思故乡，知识需要重复记忆才能掌握哦，是重复学习、还是进入下一关呢？",
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光",
          "疑是地上霜",
          "举头望明月",
          "低头思故乡"
        ],
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来学吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>\n<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>\n<s>疑是<break time=\"100ms\" /><emphasis>地</emphasis>上霜</s>\n<s>举头<break time=\"100ms\" /><emphasis>望</emphasis>明月</s>\n<s>低头<break time=\"100ms\" /><emphasis>思</emphasis>故乡</s>"
          },
          {
            "type": "PlainText",
            "source": "知识需要重复记忆才能掌握哦，是重复学习、还是进入下一关呢？"
          }
        ]
      }
    }
  ]
```

## 4.2 Read_跟读

query：我要跟读静夜思

response：

```
  "results": [
    {
      "hint": "小朋友，跟我一起来读吧，静夜思，唐代，李白，床前明月光，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来读吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>\n<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.3 Abut_对答

queyr：我要对静夜思

response：

```
  "results": [
    {
      "hint": "小朋友，跟我一起来对诗词吧，静夜思，唐代，李白，床前明月光，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来对诗词吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>\n<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.4 Recite_背

query：我要背静夜思

response：

```
  "results": [
    {
      "hint": "小朋友，你来背诗词吧，静夜思，唐代，李白，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": null,
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，你来背诗词吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.5 Next_下一关

query：下一关 （假定当前关是**对答**）

response：

```
  "results": [
    {
      "hint": "小朋友，你来背诗词吧，静夜思，唐代，李白，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": null,
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，你来背诗词吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.6 Prev_上一关

query:上一关（假定当前关是对这一关）

response：

```
  "results": [
    {
      "hint": "小朋友，跟我一起来读吧，静夜思，唐代，李白，床前明月光，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来读吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>\n<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.7 Repeat_重复

query：重复学习（假定当前关是对这一关）

response：

```
  "results": [
    {
      "hint": "小朋友，跟我一起来对诗词吧，静夜思，唐代，李白，床前明月光，小朋友，该你啦",
      "data": {
        "author": [
          "李白"
        ],
        "content": [
          "床前明月光"
        ],
        "dynasty": [
          "唐代"
        ],
        "length": 20,
        "title": "静夜思"
      },
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，跟我一起来对诗词吧"
          },
          {
            "type": "SSML",
            "source": "<p>静夜思</p>\n<p><s>唐代</s><s>李白</s></p>\n<s>床前<break time=\"100ms\" /><emphasis>明</emphasis>月光</s>"
          },
          {
            "type": "PlainText",
            "source": "小朋友，轮到你啦"
          }
        ]
      }
    }
  ]
```

## 4.8 Exit_退出

query：退出

response：

```
  "results": [
    {
      "hint": "好的",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "好的"
          }
        ]
      }
    }
  ]
```


