
# 1. 服务简介

单词互动在带屏设备上使用，采用VUI+GUI多模态交互，使小朋友在于机器人交互过程中，轻松愉快的掌握精心挑选的200个儿童必备常用词汇。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| mode | 课程or通关 | 课程 |
| num | 课程数or通关数 | 1 |

# 3.意图

## 3.1 Enter

 request: 我要学单词**课程1**
 
 response:
 
 ```
 
 ```
 
## 3.2 Wonder
  
  request: 我不知道
  
  response:(假定是在**测试**这一关）
  
  
  
## 3.3 Match
  
  request: apple
  
  response:(假定是在**测试**这一关**apple**这个单词)
  
  
  
## 3.4 Exit
  
  request: 退出
  
  response:
  
  
  
# 4.事件

## 4.1 ROSAI.EnterEvent_进入事件

request:

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

response:


## 4.2 ROSAI.TouchEvent_点击事件

request:

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

response:

## 4.3 ROSAI.TimeOutEvent_超时事件

request:

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

response:


## 4.4 ROSAI.ContinueEvent_定时跳转事件

request:

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

response:


## 4.5 ROSAI.ExitEvent_退出事件

request:

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

response:

