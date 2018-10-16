<h1 id='100'>目录</h1>

* [1. 服务简介](#1)
* [2. 槽位](#2)
* [3. 意图](#3)
* [3.1 Enter意图](#3.1)
* [3.2 Wonder意图](#3.2)
* [3.3 Match意图](#3.3)
* [3.4 Exit意图](#3.4)
* [4. 事件](#4)
* [4.1 ROSAI.EnterEvent事件](#4.1)
* [4.2 ROSAI.TouchEvent事件](#4.2)
* [4.3 ROSAI.TimeoutEvent事件](#4.3)
* [4.4 ROSAI.ContinueEvent事件](#4.4)
* [4.5 ROSAI.ExitEvent事件](#4.5)
* [5. 学练测流程示例](#5)
* [6. 通关流程示例](#6)




<h1 id='1'>1. 服务简介</h1>

单词互动在带屏设备上使用，采用VUI+GUI多模态交互，使小朋友在于机器人交互过程中，轻松愉快的掌握精心挑选的200个儿童必备常用词汇。

<h1 id='2'>2.槽位</h1>

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| mode | 课程or通关 | 课程 |
| num | 课程数or通关数 | 1 |

<h1 id='3'>3.意图</h1>

<h2 id='3.1'>3.1 Enter</h2>

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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O001"
                }
            ]
        }
    ]
 ```
 
<h2 id='3.2'>3.2 Wonder</h2>
  
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 12,
                    "code": "M002"
                }
            ]
        }
    ]
  ```
  
<h2 id='3.3'>3.3 Match</h2>
  
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
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
  ```
  
  
<h2 id='3.4'>3.4 Exit</h2>
  
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
  ```
  
  
<h1 id='4'>4. 事件</h1>

<h2 id='4.1'>4.1 ROSAI.EnterEvent_进入事件</h2>

**进入单词app：**

**request**:

```
 {
    "event": {
        "name": "ROSAI.EnterEvent",
        "type": "dedicated",
        "data": {
            "service": "AiLiveDict"
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
```
 
 
**进入具体课程或通关：**

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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O001"
                }
            ]
        }
    ]
```

<h2 id='4.2'>4.2 ROSAI.TouchEvent_点击事件</h2>

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


<h2 id='4.3'>4.3 ROSAI.TimeOutEvent_超时事件</h2>

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

<h2 id='4.4'>4.4 ROSAI.ContinueEvent_定时跳转事件</h2>

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


<h2 id='4.5'>4.5 ROSAI.ExitEvent_退出事件</h2>

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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
```

<h1 id='5'>5. “学练测”流程</h1>

### 5.1 进入单词互动app（语音或Enter事件进入）

**语音request**:

我要学单词

**Enter事件进入request**:

```
 {
    "event": {
        "name": "ROSAI.EnterEvent",
        "type": "dedicated",
        "data": {
            "service": "AiLiveDict"
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
```

### 5.2 进入具体课程或通关(语音或Enter事件进入）

**语音request**:

我要学课程1

**Enter事件进入request**:

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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O001"
                }
            ]
        }
    ]
```

### 5.2 小朋友点击卡片，客户端发送Touch事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
 ```
 
 **response**:
 
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

**备注**：每个单词在学的过程中，要点击四次；这里为减少篇幅，省略两次，体现最后一次点击

### 5.3 小朋友第四次点击卡片，客户端发送Touch事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
 ```
 
 **response**:
 
 ```
 "results": [
        {
            "hint": "apple，小朋友，你真棒！又学习了一个单词哦！我们来练习练习吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "apple，小朋友，你真棒！又学习了一个单词哦！我们来练习练习吧！"
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
                    "type": "ROSAI.EVENT",
                    "event": {
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ]
        }
    ]
 ```
 
 **备注**:云端返回results中，包含ROSAI.EVENT表示，希望1000ms后，客户端发送ROSAI.ContinueEvent事件
 
 ### 5.4 客户端1s后发送ROSAI.ContinueEvent事件
 
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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
 ```
 
 **response**:
 
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
 
  ### 5.5 小朋友语音输入“apple”
  
  **request**: apple
  
  **response**:
  
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
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
  ```
  
### 5.6 客户端1s后发送ROSAI.ContinueEvent事件

**request**:

```
"results": [
        {
            "hint": "小朋友，想知道这张卡片中的单词用英语怎么读么？和我一起读吧！apple！该你啦！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，想知道这张卡片中的单词用英语怎么读么？和我一起读吧！apple！该你啦！"
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

 ### 5.7 小朋友语音输入“apple”
  
  **request**: apple
  
  **response**:
  
  ```
      "results": [
        {
            "hint": "小朋友，你真棒！我们继续学习吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，你真棒！我们继续学习吧！"
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
                                    "imageUrl": "http://ip/star/red-card.jpg",
                                    "text": "apple",
                                    "textPosition": "center",
                                    "imagePosition": "bottom"
                                }
                            }
                        ]
                    }
                },
                {
                    "type": "ROSAI.EVENT",
                    "event": {
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
  ```
  
 ### 5.8 客户端1s后发送ROSAI.ContinueEvent事件
 
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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
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
                                "url": "http://ip/pear/front-card.jpg"
                            }
                        ]
                    }
                }
            ]
        }
    ]
 ```
 
 **备注**：这时候重新回到学的阶段，开始学习该课程中下一个单词，重复上述“学、练”步骤，直到该课程所有单词都“学、练”完成
 
 ### 5.9 假设已经是该课程最后一个单词最后一次练习，并且小朋友对答正确，等待客户端发送ROSAI.ContinueEvent事件
 
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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
 ```
 
 **response**:
 
 ```
 "results": [
        {
            "hint": "小朋友，这张卡片用英语怎么读么？试试吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，这张卡片用英语怎么读么？试试吧！"
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
                                "url": "http://ip/peach/front.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "peach",
                                    "textPosition": "center"
                                }
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
 
 **备注**:此时已经进入了测试阶段
 
 
### 5.10 小朋友语音回答

**request**: peach

**response**:

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
                                "url": "http://ip/peach/front.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "peach",
                                    "textPosition": "center"
                                }
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
                                "url": "http://ip/star/red-card.jpg"
                            }
                        ]
                    }
                },
                {
                    "type": "ROSAI.EVENT",
                    "event": {
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
```
 
### 5.11 客户端1s后发送ROSAI.ContinueEvent事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
```

**response**:

```
 "results": [
        {
            "hint": "小朋友，这张卡片用英语怎么读么？试试吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，这张卡片用英语怎么读么？试试吧！"
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
                                "url": "http://ip/banana/front-card.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "banana",
                                    "textPosition": "center"
                                }
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

**备注**:重复上述步骤，直到是本课程最后一个单词

### 5.11 假设现在是该课程在测试阶段最后一个单词，并且小朋友答对了，客户端1s后发送ROSAI.ContinueEvent事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，你真棒！本课程的单词掌握了5个！我们继续学习吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，你真棒！本课程的单词掌握了5个！我们继续学习吧！"
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
                                "url": "http://ip/star/5red-card.jpg"
                            }
                        ]
                    }
                },
                {
                    "type": "ROSAI.EVENT",
                    "event": {
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ]
        }
    ]
```

**备注**:等待客户端发送ROSAI.ContinueEvent事件

### 5.12 客户端1s后发送ROSAI.ContinueEvent事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，见到你真开心！我们一起来学单词吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，见到你真开心！我们一起来学单词吧！"
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

**备注**:这里就是回到主页了。

* [回到目录](#100)

<h1 id='6'>6. “通关”流程</h1>

### 6.1 小朋友说“我要学单词通关1”

**request**：

```
{
    "agentId":"GExZTRmMGY2NTg1N",
    "token":"cdf6da8b3a7c2b652bbeaf720d3278b89689",
    "sessionId":"4000007700000002",
    "query":"我要学单词通关1"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，这张卡片用英语怎么读么？试试吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，这张卡片用英语怎么读么？试试吧！"
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
                                "url": "http://ip/orange/front.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "orange",
                                    "textPosition": "center"
                                }
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O002"
                }
            ]
        }
    ]
```

### 6.2 小朋友说“orange”

**request**:

```
{
    "agentId":"GExZTRmMGY2NTg1N",
    "token":"cdf6da8b3a7c2b652bbeaf720d3278b89689",
    "sessionId":"4000007700000002",
    "query":"orange"
}
```
**response**:

```
"results": [
        {
            "hint": "小朋友，这张卡片用英语怎么读么？试试吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，这张卡片用英语怎么读么？试试吧！"
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
                                "url": "http://ip/bike/front-card.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "bike",
                                    "textPosition": "center"
                                }
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O002"
                }
            ]
        }
    ]
```

### 6.3 小朋友说“我不知道”

**request**:

```
{
    "agentId":"GExZTRmMGY2NTg1N",
    "token":"cdf6da8b3a7c2b652bbeaf720d3278b89689",
    "sessionId":"4000007700000002",
    "query":"我不知道"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，这张卡片用英语怎么读么？试试吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，这张卡片用英语怎么读么？试试吧！"
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
                                "url": "http://ip/ship/front-card.jpg"
                            },
                            {
                                "url": "http://ip/backgroud/no_color.jpg",
                                "bulletScreen": {
                                    "text": "ship",
                                    "textPosition": "center"
                                }
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
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 14,
                    "code": "O002"
                }
            ]
        }
    ]
```

**备注**：一个通关包含前边两个课程的单词，现在一个课程是5个单词，所以一个通关共10个单词，重复上述步骤，直到最后一个单词


### 6.4 假设目前是通过最后一个单词，并且是等待小朋友回复的状态

**request**:（小朋友回答最后一个单词后，会计算学习成绩，显示勋章和红旗）

```
{
    "agentId":"GExZTRmMGY2NTg1N",
    "token":"cdf6da8b3a7c2b652bbeaf720d3278b89689",
    "sessionId":"4000007700000002",
    "query":"boat"
}
```

**response**:

```
"results": [
        {
            "hint": "小朋友，表现不错！这一关的单词学得很好！我们继续挑战下一关吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，表现不错！这一关的单词学得很好！我们继续挑战下一关吧！"
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
                                "url": "http://ip/medal/front-card.jpg"
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
                                "url": "http://ip/flag/2red-card.jpg"
                            }
                        ]
                    }
                },
                {
                    "type": "ROSAI.EVENT",
                    "event": {
                        "name": "ROSAI.ContinueEvent",
                        "period": 1000
                    }
                }
            ],
            "emotions": [
                {
                    "type": "answer",
                    "level": 0,
                    "code": "A001"
                }
            ]
        }
    ]
```

### 6.5 客户端1s后发送ROSAI.ContinueEvent事件

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
    "clientId": "4000007700000002",
    "agentId": "GExZTRmMGY2NTg1N",
    "token": "3bb83ed5c756800c81b1635de10defc3"
}
```

**response**: （回到单词互动首页）

```
"results": [
        {
            "hint": "小朋友，见到你真开心！我们一起来学单词吧！",
            "outputSpeech": {
                "items": [
                    {
                        "type": "PlainText",
                        "source": "小朋友，见到你真开心！我们一起来学单词吧！"
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
                                    "text": "水果2",
                                    "textPosition": "bottom"
                                }
                            },
                            {
                                "url": "http://ip/lession4/home.jpg",
                                "bulletScreen": {
                                    "text": "交通2",
                                    "textPosition": "bottom"
                                }
                            },
                            {
                                "url": "http://ip/gate2/home.jpg",
                                "bulletScreen": {
                                    "text": "通关",
                                    "textPosition": "bottom"
                                }
                            }
                        ]
                    }
                }
            ]
        }
    ]
```

* [回到目录](#100)

