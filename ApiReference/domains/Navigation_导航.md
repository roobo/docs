# 1.服务背景

Goals

导航和搜索周边的语义服务。

Requirement

| No. | Function | Description |
| --- | --- | --- |
| 1 | 导航 | 输出导航意图和参数 |
| 2 | 搜索 | 输出搜索意图和参数 |

## 2. 槽位

| Slot\_Key | Description | Main\_Application | Example |
| --- | --- | --- | --- |
| locations | 地点列表 | 用于导航，搜索等。返回结果时会将其拆分成location，name，street，building number | 清华大学南门 海淀区 肯德基 北苑路和春华路交叉口 |
| location\_reference | 方位词 | 用户导航，搜索等 | 前方 目的地 |
| traffic\_category | 交通类型 | 用户导航，搜索等 | 路口 交叉口 |
| price\_modifier | 价格修饰词 | 用户导航，搜索等 | 便宜的 性价比高的 |
| quality\_modifier | 质量修饰词 | 用户导航，搜索等 | 好的 很赞的 |

# 3.意图

## 3.1 Navigate\_导航

导航意图关键词：\[导航\|导航去\|导航到\|要去\|要到\|带我去\|带我到\|载我去\|载我到\|开车去\|开车到\|驾车去\|驾车到\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 导航意图关键词+&lt;location\_reference&gt; | 导航到目的地 |
| 导航意图关键词+&lt;traffic\_category&gt; | 导航到交叉口 |
| 导航意图关键词+&lt;locations&gt; | 导航到清华大学东门 |
| 导航意图关键词+&lt;price\_modifier&gt;+&lt;locations&gt; | 导航到便宜的咖啡馆 |
| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;locations&gt; | 导航到很赞的餐馆 |
| 导航意图关键词+&lt;traffic\_category&gt;+&lt;locations&gt; | 导航到路口的火锅店 |
| 导航意图关键词+&lt;location\_reference&gt;+&lt;locations&gt; | 导航到前方的超市 |
| 导航意图关键词+&lt;price\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 导航到便宜的街边的餐馆 |
| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 导航到质量好的路口的超市 |
| 导航意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; | 导航到便宜的附近的商场 |
| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; | 导航到低价的前方的酒店 |
| 导航意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 导航到便宜的前方路口的餐厅 |
| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 导航到很棒的前方路口的西餐厅 |

## 3.2 Search\_搜索

搜索意图关键词：\[搜索\|搜\|搜搜\|查\|查查\|查找\|查询\|找\|找找\|寻找\|发现\|有没有\|搜寻\|显示\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 搜索意图关键词+&lt;locations&gt; | 搜索清华大学东门 |
| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;locations&gt; | 搜索便宜的咖啡馆 |
| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;locations&gt; | 搜索很赞的餐馆 |
| 搜索意图关键词+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索路口的火锅店 |
| 搜索意图关键词+&lt;location\_reference&gt;+&lt;locations&gt; | 搜索前方的超市 |
| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索便宜的街边的餐馆 |
| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索质量好的路口的超市 |
| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; | 搜索便宜的附近的商场 |
| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; | 搜索低价的前方的酒店 |
| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索便宜的前方路口的餐厅 |
|  |  |
| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索很棒的前方路口的西餐厅 |

# 4.返回结果

## 4.1 Navigate\_导航

| **Field\_Name** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- |
| hint | 提示语 | 将为您导航到五道口 |
| intent | 意图名 | Navigate |
| location\_reference | 方位词 | 前方 |
| locations | 地点数组 | \[北京市 海淀区 华清嘉园\] |
| streets | 街道名 | 北苑路 |
| names | 具体名称数组 | 海底捞 |
| building\_num | 楼牌号 | 9号楼 |
| price\_modifier | 价格修饰词 | 便宜 |
| quality\_modifier | 质量修饰词 | 好 |
| search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
| traffic\_category | 交通类型 | 拐角 |
| formatType | 结果类型 | text |

```
"result": {
        "hint": "将为您导航到北京市海淀区华清嘉园火锅店",
        "data": {
            "intent": "Navigate",
            "location_reference": "附近",
            "locations": [
                "北京市",
                "华清嘉园",
                "海淀区"
            ],
            "names": [
                "火锅店"
            ],
            "price_modifier": "便宜",
            "quality_modifier": "",
            "search_phrase": "北京市海淀区华清嘉园火锅店",
            "traffic_category": ""
        },
        "formatType": "text"
    }
```

## 4.2 Search\_搜索

| **Field\_Name** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- |
| hint | 提示语 | 将为您导航到五道口 |
| intent | 意图名 | Search |
| location\_reference | 方位词 | 前方 |
| locations | 地点数组 | \[北京市 海淀区 华清嘉园\] |
| streets | 街道名 | 北苑路 |
| names | 具体名称数组 | 海底捞 |
| building\_num | 楼牌号 | 9号楼 |
| price\_modifier | 价格修饰词 | 便宜 |
| quality\_modifier | 质量修饰词 | 好 |
| search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
| traffic\_category | 交通类型 | 拐角 |
| formatType | 结果类型 | text |

```

"result": {
         "hint": "将为您搜索北京市海淀区华清嘉园火锅店",
         "data": {
         "intent": "Search",
         "location_reference": "附近",
         "locations": [
             "北京市",
             "华清嘉园",
             "海淀区"
          ],
         "names": [
             "火锅店"
           ],
         "price_modifier": "便宜",
         "quality_modifier": "",
         "search_phrase": "北京市海淀区华清嘉园火锅店",
         "traffic_category": ""
         },
         "formatType": "text"
     }
```

