# 1.服务背景

Goals

导航和搜索周边的语义服务。

Requirement

| No. | Function | Description |
| --- | --- | --- |
| 1 | 导航 | 输出导航意图和参数 |
| 2 | 搜索 | 输出搜索意图和参数 |

## 2. 槽位

| Slot_Key | Description | Main_Application | Example |
| --- | --- | --- | --- |
| locations | 地点列表 | 用于导航，搜索等。返回结果时会将其拆分成location，name，street，building number | 清华大学南门 海淀区 肯德基 北苑路和春华路交叉口 |
| location_reference | 方位词 | 用户导航，搜索等 | 前方 目的地 |
| traffic_category | 交通类型 | 用户导航，搜索等 | 路口 交叉口 |
| price_modifier | 价格修饰词 | 用户导航，搜索等 | 便宜的 性价比高的 |
| quality_modifier | 质量修饰词 | 用户导航，搜索等 | 好的 很赞的 |

# 3.意图

## 3.1 Navigate\_导航

导航意图关键词：\[导航\|导航去\|导航到\|要去\|要到\|带我去\|带我到\|载我去\|载我到\|开车去\|开车到\|驾车去\|驾车到\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 导航意图关键词+&lt;location\_reference&gt; | 导航到目的地 |
| 导航意图关键词+&lt;traffic\_category&gt; | 导航到交叉口 |
| 导航意图关键词+&lt;locations&gt; | 导航到清华大学东门 |

导航到奥林匹克森林公园 \|
\| 导航意图关键词+&lt;price\_modifier&gt;+&lt;locations&gt; \| 导航到便宜的咖啡馆 \|
\| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;locations&gt; \| 导航到很赞的餐馆 \|
\| 导航意图关键词+&lt;traffic\_category&gt;+&lt;locations&gt; \| 导航到路口的火锅店 \|
\| 导航意图关键词+&lt;location\_reference&gt;+&lt;locations&gt; \| 导航到前方的超市 \|
\| 导航意图关键词+&lt;price\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 导航到便宜的街边的餐馆 \|
\| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 导航到质量好的路口的超市 \|
\| 导航意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; \| 导航到便宜的附近的商场 \|
\| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; \| 导航到低价的前方的酒店 \|
\| 导航意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 导航到便宜的前方路口的餐厅 \|
\| 导航意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 导航到很棒的前方路口的西餐厅 \|

## 3.2 Search\_搜索

搜索意图关键词：\[搜索\|搜\|搜搜\|查\|查查\|查找\|查询\|找\|找找\|寻找\|发现\|有没有\|搜寻\|显示\]

| **Support\_Semantic** | **Example** |
| --- | --- |
| 搜索意图关键词+&lt;locations&gt; | 搜索清华大学东门 |

搜索奥林匹克森林公园 \|
\| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;locations&gt; \| 搜索便宜的咖啡馆 \|
\| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;locations&gt; \| 搜索很赞的餐馆 \|
\| 搜索意图关键词+&lt;traffic\_category&gt;+&lt;locations&gt; \| 搜索路口的火锅店 \|
\| 搜索意图关键词+&lt;location\_reference&gt;+&lt;locations&gt; \| 搜索前方的超市 \|
\| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 搜索便宜的街边的餐馆 \|
\| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 搜索质量好的路口的超市 \|
\| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; \| 搜索便宜的附近的商场 \|
\| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;locations&gt; \| 搜索低价的前方的酒店 \|
\| 搜索意图关键词+&lt;price\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 搜索便宜的前方路口的餐厅 \|
\| 搜索意图关键词+&lt;quality\_modifier&gt;+&lt;location\_reference&gt;+&lt;traffic\_category&gt;+&lt;locations&gt; \| 搜索很棒的前方路口的西餐厅 \|

# 4.返回结果

## 4.1 Navigate\_导航

| **Query** | **Result** | **Fields\_Description** |
| --- | --- | --- |
| 导航去北京市海淀区华清嘉园 |

附近的性价比高的火锅店 \| "result": {
        "hint": "将为您导航到北京市海淀区华清嘉园火锅店",
        "data": {
            "intent": "Navigate",
            "location\_reference": "附近",
            "locations": \[
                "北京市",
                "华清嘉园",
                "海淀区"
            \],
            "names": \[
                "火锅店"
            \],
            "price\_modifier": "便宜",
            "quality\_modifier": "",
            "search\_phrase": "北京市海淀区华清嘉园火锅店",
            "traffic\_category": ""
        },
        "formatType": "text"
    } \| hint：语音播报tts
formatType:数据格式
data：导航具体数据
其中：
intent: 意图
location\_reference:方位词
locations:地点数组
names:具体名称，类别等
streets:街道名
building\_num:楼牌号
price\_modifier:价格修饰词
quality\_modifier:质量修饰词
search\_phrase:搜索关键词
traffic\_category:交通类型 \|
\| 带我去路边的质量好的西餐厅 \| "result": {
        "hint": "将为您导航到西餐厅",
        "data": {
            "intent": "Navigate",
            "location\_reference": "",
            "names": \[
                "西餐厅"
            \],
            "price\_modifier": "",
            "quality\_modifier": "好",
            "search\_phrase": "西餐厅",
            "traffic\_category": "路口"
        },
        "formatType": "text"
    } \|  \|
\| 载我去目的地 \| "result": {
        "hint": "将为您导航到目的地",
        "data": {
            "intent": "Navigate",
            "location\_reference": "",
            "names": \[
                "目的地"
            \],
            "price\_modifier": "",
            "quality\_modifier": "",
            "search\_phrase": "目的地",
            "traffic\_category": ""
        },
        "formatType": "text"
    } \|  \|
\| 带我去西王庄9号楼 \| "result": {
        "hint": "将为您导航到西王庄9号楼",
        "data": {
            "building\_num": \[
                "9号楼"
            \],
            "intent": "Navigate",
            "location\_reference": "",
            "locations": \[
                "西王庄"
            \],
            "price\_modifier": "",
            "quality\_modifier": "",
            "search\_phrase": "西王庄9号楼",
            "traffic\_category": ""
        },
        "formatType": "text"
    } \|  \|

4.2 Search\_搜索

| **Query** | **Result** | **Fields\_Description** |
| --- | --- | --- |
| 查找春华路和北苑路交叉口 | "result": { |

```
    "hint": "将为您查找春华路和北苑路",
    "data": {
        "intent": "Search",
        "location\_reference": "",
        "locations": \[
            "北苑路",
            "春华路"
        \],
        "price\_modifier": "",
        "quality\_modifier": "",
        "search\_phrase": "春华路和北苑路",
        "traffic\_category": "交叉"
    },
    "formatType": "text"
} | hint：语音播报tts
```

formatType:数据格式
data：导航具体数据
其中：
intent: 意图
location\_reference:方位词
locations:地点数组
names:具体名称，类别等
streets:街道名
building\_num:楼牌号
price\_modifier:价格修饰词
quality\_modifier:质量修饰词
search\_phrase:搜索关键词
traffic\_category:交通类型 \|

