# 1.服务背景

实时英译汉

# 2.槽位

| Slot\_Key | Description | Main\_Application | Example |
| --- | --- | --- | --- |
| englishword | 待翻译英文语句 |  | hello |

# 3.意图

## 3.1 Enter\_进入

意图关键词：[我要|我想|帮我|给我|]英译[汉|中]

## 3.2 EntoZhTranslate\_翻译

意图关键词：任意英文句子

## 3.3 Exit\_退出

意图关键词：goodbye

# 4.返回结果

## 4.1 Enter\_进入

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | 好的，从现在起主人和我说英文，我来给主人翻译成中文，想结束时请和我说goodbye |

```
  "results": [
    {
      "hint": "好的，从现在起主人和我说英文，我来给主人翻译成中文，想结束时请和我说goodbye"
    }
  ]
```

## 4.2 EntoZhTranslate\_翻译

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | 你好 |
| data |  |  |  |
|  | destlang | 回复语语种 | zh |
|  | destword | 翻译结果 | hello |
|  | srcword | 待翻译语句 | 你好 |

```
 "results": [
    {
      "hint": "你好",
      "data": {
        "destlang": "zh",
        "destword": "你好",
        "srcword": "hello"
      }
    }
  ]
```

## 4.3 Exit\_退出

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 回复语 | 好的，下次再找我吧 |

```
  "results": [
    {
      "hint": "好的，下次再找我吧"
    }
  ]
```
