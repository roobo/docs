# 1. 服务简介

为用户提供翻译服务，资源来自百度翻译\/有道翻译API，可以提供21种语言的翻译。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| word | 用户需要翻译的词 | 苹果 |
| lang | 语言 | 英语、法语 |

# 3.意图


## 3.1 Translate_翻译

我要翻译 

能帮我翻译**英文**么 

**苹果**用**英语**怎么说


## 3.2 Repeat_重复

重复一遍 

## 3.3 Change_切换

(换一种说法，针对同一个源单词有不同的翻译结果的情况)

换种说法 


## 3.4 Spell_拼写

(拼写意图，只针对翻译结果为英文的情况，翻译结果\(dstword\)字段为单词拆分为字母的结果)

拼写一遍

## 3.5 SpeedUp_大声

说快一点

## 3.6 SpeedDown_小声

说慢一点

## 3.7 Exit_退出

退出

# 4.返回结果

\*\*\*由于Translate意图、Repeat意图、Change意图和Spell意图返回字段相同，在此统一说明


| **Field\_Name** | **Sub\_Field** | **Field\_Description** | **Field\_Type** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |    | 回复语 | string | 我会说英语、俄语、法语等多种语言，你要翻译成哪一种呢？ |
| data |    |     |     |     |
|    | destlang | 回复语种 | string | en |
|    | dstword | 翻译结果 | string | apple |
|    | speed | 语速 | string |    |
|    | srclang | 源语言 | string | zh |
|    | srcword | 待翻译词汇 | string | 苹果 |
|    | url | 翻译结果音频 | string | http://dwn.roo.bo/voices/translate/a/apple.wav |
|    | volume | 音量 | string |  |

## 4.1 Translate_翻译

返回样例

```
   "results": [
    {
      "hint": "Apple,A p p l e",
      "data": {
        "destlang": "en",
        "dstword": "Apple,A p p l e",
        "speed": "",
        "srclang": "zh",
        "srcword": "苹果",
        "url": "http://dwn.roo.bo/voices/translate/a/apple.wav",
        "volume": ""
      }
    }
  ]
```

**故事机和布丁方案**下，“我要翻译”默认进入英文翻译。

返回样例

```
 "results": [
    {
      "hint": "好的，现在起我会连续将你说的每句话翻译成英语，想结束时可以对我说退出，我们开始吧"
    }
  ]
```

## 4.2 Repeat_重复

返回样例

```
  "results": [
    {
      "hint": "Apple,A p p l e",
      "data": {
        "destlang": "en",
        "dstword": "Apple",
        "speed": "",
        "srclang": "zh",
        "srcword": "苹果",
        "url": "http://dwn.roo.bo/voices/translate/a/apple.wav",
        "volume": ""
      }
    }
  ]
```

## 4.3 Change_切换

返回样例

```
  "results": [
    {
      "hint": "Iphone",
      "data": {
        "destlang": "en",
        "dstword": "Iphone",
        "speed": "",
        "srclang": "zh",
        "srcword": "苹果",
        "url": "",
        "volume": ""
      }
    }
  ]
```

## 4.4 Spell_拼写

```
  "results": [
    {
      "hint": "I p h o n e",
      "data": {
        "destlang": "en",
        "dstword": "I p h o n e",
        "speed": "",
        "srclang": "zh",
        "srcword": "苹果",
        "url": "",
        "volume": ""
      }
    }
  ]
```

## 4.5 SpeedUp_大声

返回样例

```
  "results": [
    {
      "hint": "好的，我会快点说"
    }
  ]
```

## 4.6 SpeedDown_小声

返回样例

```
  "results": [
    {
      "hint": "好的，我会慢点说"
    }
  ]
```

## 4.7 Exit_退出
```
  "results": [
    {
      "hint": "好的，下次翻译再找我吧"
    }
  ]
```
