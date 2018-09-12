
# 1. 服务简介

单词互动在带屏设备上使用，采用VUI+GUI多模态交互，使小朋友在于机器人交互过程中，轻松愉快的掌握精心挑选的200个儿童必备常用词汇。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| mode | 课程or通关 | 课程 |
| num | 课程数or通关数 | 1 |

# 3.意图

## 3.1 Enter

 **request**: 我要学单词**课程1**
 
 **response**:
 
 ```
 "results": [
    {
      "hint": "小朋友，想知道这张卡片用英语怎么读么？点击卡片试试吧！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，想知道这张卡片用英语怎么读么？点击卡片试试吧！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/apple/front-card.jpg"
              }
            ]
          }
        }
      ]
    }
  ]
 ```
 
## 3.2 Wonder
  
  **request**: 我不知道
  
  **response**:(假定是在**第一次练习**这一关的第一次回复）
  
  ```
   "results": [
    {
      "hint": "没关系，我们再来读一次吧！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "没关系，我们再来读一次吧！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/apple/front-card.jpg"
              }
            ]
          }
        },
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/mike/twinkle-card.jpg"
              }
            ]
          }
        }
      ]
    }
  ]
  ```
  
  
  
## 3.3 Match
  
  **request**: apple
  
  **response**:(假定是在**第一次练习**这一关**apple**这个单词的第一次回复)
  
  ```
  "results": [
    {
      "hint": "小朋友，你真棒！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，你真棒！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/apple/front-card.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/star/red-card.jpg",
                  "imagePosition": "bottom"
                }
              }
            ]
          }
        },
        {
          "type": "ROSAI.EVENT",
          "event": {
            "name": "Continue",
            "period": 2000
          }
        }
      ]
    }
  ]
  ```
  
  
  
## 3.4 Exit
  
  **request**: 退出
  
  **response**:（回到首页）
  
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
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/lession1/home.jpg",
                "bulletScreen": {
                  "text": "水果1",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/lession2/home.jpg",
                "bulletScreen": {
                  "text": "交通1",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/gate1/homejpg",
                "bulletScreen": {
                  "text": "通关",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/lession3/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              },
              {
                "url": "http://ip/lession4/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              },
              {
                "url": "http://ip/gate2/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              }
            ]
          }
        }
      ]
    }
  ]
  ```
  
  
  
# 4.事件

## 4.1 ROSAI.EnterEvent_进入事件

**request**:

```
 {
    "event": {
        "name": "ROSAI.EnterEvent",
        "type": "dedicated",
        "data": {
            "service": "AiLiveDict",
            "parameters": {
                "mode": {
                    "orgin": "课程",
                    "normType": "String",
                    "norm": "课程"
                },
                "num": {
                    "orgin": "1",
                    "normType": "String",
                    "norm": "1"
                }
            }
        }
    },
    "clientId": "4000007700000001",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "5cfe63e08559bceea7debc06fc5d7333"
}
```

**response**:

```
"results": [
    {
      "hint": "小朋友，想知道这张卡片用英语怎么读么？点击卡片试试吧！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，想知道这张卡片用英语怎么读么？点击卡片试试吧！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/apple/front-card.jpg"
              }
            ]
          }
        }
      ]
    }
  ]
```


## 4.2 ROSAI.TouchEvent_点击事件

**request**:

```
{
    "event": {
        "name": "ROSAI.TouchEvent",
        "type": "dedicated",
        "data" : {
          "service": "AiLiveDict"
        }
    },
    "clientId": "4000007700000001",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "5cfe63e08559bceea7debc06fc5d7333"
}
```

**response**:（假定是学这一关的第一次点击）

```
"results": [
    {
      "hint": "apple，小朋友，想知道这张卡片中的单词长什么样子么？点击卡片试试吧！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "apple，小朋友，想知道这张卡片中的单词长什么样子么？点击卡片试试吧！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/backgroud/no_color.jpg",
                "bulletScreen": {
                  "text": "apple",
                  "textPosition": "center"
                }
              }
            ]
          }
        }
      ]
    }
  ]
```

## 4.3 ROSAI.TimeOutEvent_超时事件

**request**:

```
{
    "event": {
        "name": "ROSAI.TimeoutEvent",
        "type": "dedicated",
        "data" : {
          "service": "AiLiveDict"
        }
    },
    "params": {
      "repeat": 0
    },
    "clientId": "4000007700000001",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "5cfe63e08559bceea7debc06fc5d7333"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，我找不到你了，我们下次再来玩吧",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，我找不到你了，我们下次再来玩吧"
                    }
                ]
            }
        }
    ]
```


## 4.4 ROSAI.ContinueEvent_定时跳转事件

**request**:

```
{
    "event": {
        "name": "ROSAI.ContinueEvent",
        "type": "dedicated",
        "data" : {
          "service": "AiLiveDict"
        }
    },
    "clientId": "4000007700000001",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "5cfe63e08559bceea7debc06fc5d7333"
}
```

**response**:(假定在**学**这关第四次点击后，需要定时跳转)

```
"results": [
    {
      "hint": "小朋友，想知道这张卡片用英语怎么读么？和我一起读吧！apple！该你啦！",
      "outputSpeech": {
        "items": [
          {
            "type": "PlainText",
            "source": "小朋友，想知道这张卡片用英语怎么读么？和我一起读吧！apple！该你啦！"
          }
        ]
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/apple/front-card.jpg"
              }
            ]
          }
        },
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/mike/twinkle-card.jpg"
              }
            ]
          }
        }
      ]
    }
  ]
```


## 4.5 ROSAI.ExitEvent_退出事件

**request**:

```
{
    "event": {
        "name": "ROSAI.ExitEvent",
        "type": "dedicated",
        "data" : {
          "service": "AiLiveDict"
        }
    },
    "clientId": "4000007700000001",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "5cfe63e08559bceea7debc06fc5d7333"
}
```

**response**:（回到首页）

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
      },
      "directives": [
        {
          "type": "Display.Customized",
          "card": {
            "type": "Images",
            "list": [
              {
                "url": "http://ip/lession1/home.jpg",
                "bulletScreen": {
                  "text": "水果1",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/lession2/home.jpg",
                "bulletScreen": {
                  "text": "交通1",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/gate1/homejpg",
                "bulletScreen": {
                  "text": "通关",
                  "textPosition": "bottom"
                }
              },
              {
                "url": "http://ip/lession3/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              },
              {
                "url": "http://ip/lession4/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              },
              {
                "url": "http://ip/gate2/home.jpg",
                "bulletScreen": {
                  "imageUrl": "http://ip/lock/light_colour.jpg",
                  "imagePosition": "full"
                }
              }
            ]
          }
        }
      ]
    }
  ]
```

