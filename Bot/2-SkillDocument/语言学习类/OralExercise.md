# 1.服务背景

英文口语对练

## 2. 槽位

| Slot\_Key | Description | Main\_Application | Example |
| --- | --- | --- | --- |
| query | 英文对练语句 |  | what is your name |

# 3.意图

## 3.1 Enter\_进入

意图关键词：[打开][英语对练|对练|英语聊天]

## 3.2 Exercise\_练习

意图关键词：任意英文句子

## 3.3 Exit\_退出

意图关键词：goodbye

# 4.返回结果

## 4.1 Enter\_进入

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | 好的，从现在起我们开始用英语对话，想退出时请和我说goodbye |
| data |  |  |  |
|  | destlang | 回复语语种 | en |

```
"results": [
  {
    "hint": "好的，从现在起我们开始用英语对话，想退出时请和我说goodbye",
    "data": {
      "destlang": "zh"
    }
  }
]
```

## 4.2 Exercise\_练习

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | Hi once again! I study at a roboschool and all our students have to travel to another planet. I've decided to come to Earth. |
| data |  |  |  |
|  | destlang | 回复语语种 | en |

```
"results": [
  {
    "hint": "Hi once again! I study at a roboschool and all our students have to travel to another planet. I've decided to come to Earth.",
    "data": {
      "destlang": "en"
    }
  }
]
```

## 4.3 Exit\_退出

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | 好的，再见 |
| data |  |  |  |
|  | destlang | 回复语语种 | en |

```
"results": [
  {
    "hint": "好的，再见",
    "data": {
      "destlang": "zh"
    }
  }
]
```
