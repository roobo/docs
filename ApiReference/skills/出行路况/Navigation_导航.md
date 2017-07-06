# 1.服务背景

导航和搜索周边的语义服务。

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
| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 搜索很棒的前方路口的西餐厅 |

## 3.3 Traffic\_路况

路况关键词模版1：\[交通\|路况\|车\|路上\]\[情况\|状态\|信息\|流量\|\]\[怎么样\|好么\|多么\|大么\|顺畅么\|堵么\|堵不堵\|如何\]

路况关键词模版2：\[是否通畅\|开过去顺畅么\|是否顺畅\|塞车么\|会不会堵\|堵吗\|堵车吗\|会不会堵车\|堵的严重吗\|堵的严不严重\|开过去通畅么\|是否塞车\|会不会塞车\|堵不堵\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| &lt;location&gt;+路况关键词模版1 | 清华大学东门路况如何 |
| &lt;location&gt;+路况关键词模版2 | 北苑路堵不堵 |
| &lt;location\_reference&gt;+ &lt;location&gt;+路况关键词模版1 | 附近的咖啡店堵不堵 |
| &lt;location\_reference&gt;+ &lt;location&gt;+路况关键词模版2 | 沿途的酒店路况怎么样 |
| &lt;traffic\_category&gt;+&lt;locations&gt;+路况关键词模版1 | 路边的餐馆堵不堵 |
| &lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt;+路况关键词模版1 | 前方路口的咖啡厅交通怎么样 |
| &lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt;+路况关键词模版2 | 附近的酒店是否通畅 |
| \[从\]+&lt;locations&gt;+\[到\|往\|去往\]+&lt;locations&gt;+路况关键词模版1 | 从北京大学东门到知春路交通堵不堵 |
| \[从\]+&lt;locations&gt;+\[到\|往\|去往\]+&lt;locations&gt;+路况关键词模版2 | 从清华大学西门到中关村会不会塞车 |

## 3.4 Time\_时长

时长前缀模版：\[大概\|\]\[需要\|要\|\]\[多久\|多长时间\|多少时候\|什么时候\|几个钟头\|几个小时\]\[我\|\]\[能\|能够\|\]\[到\|到达\|抵达\]

时长后缀模版：\[需要\|要\|\]\[多久\|多长时间\|多少时候\|什么时候\|几个钟头\|几个小时\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 去&lt;location&gt;+时长后缀模版 | 去清华大学东门需要多久 |
| 时长前缀模版+&lt;location&gt; | 多久能到北苑路 |
| 时长前缀模版&lt;location\_reference&gt;+ &lt;location&gt; | 多久能到附近的咖啡店 |
| 到&lt;location\_reference&gt;+ &lt;location&gt;+时长后缀模版 | 到沿途的酒店需要多长时间 |
| 到&lt;traffic\_category&gt;+&lt;locations&gt;+时长后缀模版 | 到路边的餐馆要多久 |
| 到&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt;+时长后缀模版 | 到前方路口的咖啡厅需要几个钟头 |
| 时长前缀模版&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; | 需要多久到附近的酒店 |
| \[从\]+&lt;locations&gt;+\[到\|往\|去往\]+&lt;locations&gt;+时长后缀模版 | 从北京大学东门到知春路要多长时间 |
| 时长前缀模版+\[从\]+&lt;locations&gt;+\[到\|往\|去往\]+&lt;locations&gt; | 多久能从清华大学西门到中关村 |

# 4.返回结果

## 4.1 Navigate\_导航

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 提示语 | 将为您导航到北京市海淀区华清嘉园火锅店 |
| data |  |  |  |
|  | intent | 意图名 | Navigate |
|  | location\_reference | 方位词 | 前方 |
|  | locations | 地点数组 | \[北京市 海淀区 华清嘉园 |
|  | streets | 街道名 | 北苑路 |
|  | names | 具体名称数组 | 海底捞 |
|  | building\_num | 楼牌号 | 9号楼 |
|  | price\_modifier | 价格修饰词 | 便宜 |
|  | quality\_modifier | 质量修饰词 | 好 |
|  | search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
|  | traffic\_category | 交通类型 | 拐角 |
| formatType |  | 结果类型 | text |

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

| **Field\_Name** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| hint |  | 提示语 | 将为您搜索北京市海淀区华清嘉园火锅店 |
| data |  |  |  |
|  | intent | 意图名 | Search |
|  | location\_reference | 方位词 | 前方 |
|  | locations | 地点数组 | \[北京市 海淀区 华清嘉园 |
|  | streets | 街道名 | 北苑路 |
|  | names | 具体名称数组 | 海底捞 |
|  | building\_num | 楼牌号 | 9号楼 |
|  | price\_modifier | 价格修饰词 | 便宜 |
|  | quality\_modifier | 质量修饰词 | 好 |
|  | search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
|  | traffic\_category | 交通类型 | 拐角 |
| formatType |  | 结果类型 | text |

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

## 4.3 Traffic\_路况

| **Field\_Name** | **Sub\_Field** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  |  | 提示语 | 将为您查询从华清嘉园到牡丹园的路况 |
| data |  |  | 返回数据 |  |
|  | intent | 意图名 | Search |  |
|  | dest |  |  |  |
|  |  | location\_reference | 方位词 | 前方 |
|  |  | locations | 地点数组 | \[北京市 海淀区 华清嘉园\] |
|  |  | streets | 街道名 | 北苑路 |
|  |  | names | 具体名称数组 | 海底捞 |
|  |  | building\_num | 楼牌号 | 9号楼 |
|  |  | search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
|  |  | traffic\_category | 交通类型 | 拐角 |
|  | origin |  |  |  |
|  |  | location\_reference | 方位词 | 前方 |
|  |  | locations | 地点数组 | \[北京市 海淀区 华清嘉园\] |
|  |  | streets | 街道名 | 春华路 |
|  |  | names | 具体名称数组 | 面面俱到 |
|  |  | building\_num | 楼牌号 | 10号楼 |
|  |  | search\_phrase | 搜索关键词 | 北京市海淀区华清嘉园 |
|  |  | traffic\_category | 交通类型 | 拐角 |
| formatType |  |  | 结果类型 | text |

## 4.4 Time\_时长

| **Field\_Name** | **Sub\_Field** | **Sub\_Field** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  |  | 提示语 | 将为您计算从五道口到牡丹园的时长 |
| data |  |  | 返回数据 |  |
|  | intent | 意图名 | Search |  |
|  | dest |  |  |  |
|  |  | location\_reference | 方位词 | 前方 |
|  |  | locations | 地点数组 |  华清嘉园 |
|  |  | streets | 街道名 |  |
|  |  | names | 具体名称数组 |  |
|  |  | building\_num | 楼牌号 |  |
|  |  | search\_phrase | 搜索关键词 | 牡丹园 |
|  |  | traffic\_category | 交通类型 |  |
|  | origin |  |  |  |
|  |  | location\_reference | 方位词 | 前方 |
|  |  | locations | 地点数组 | 五道口 |
|  |  | streets | 街道名 |  |
|  |  | names | 具体名称数组 |  |
|  |  | building\_num | 楼牌号 |  |
|  |  | search\_phrase | 搜索关键词 |  |
|  |  | traffic\_category | 交通类型 |  |
| formatType |  |  | 结果类型 | text |

