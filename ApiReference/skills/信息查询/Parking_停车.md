
# 1. 服务简介

停车服务，查询附近的停车场信息，查询车位情况\/收费信息

# 2.意图

### \/Search

查询附近的停车场信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;lot_count&gt; | 查找附近的三个停车场 |
| &lt;spec_dst&gt; | 查找目的地附近的停车场 |

_举例：数据部分_
```
查找附近的停车场
  "results": [
    {
      "hint": "为你推荐附近3个停车场，你可以选择任意一个查看详细信息。第1个北科创业大厦地下停车库距离63米，第2个北科创业大厦地面停车场距离67米，第3个领地地面停车场距离69米"
    }
  ]  
```

---


### \/Choose
第二个

_举例：数据部分_
```
  "results": [
    {
      "hint": "北科创业大厦地面停车场为完全对外开放地面停车场，入口位于北苑路，距离当前位置67米，为你找到入口照片。你可以查看大图或直接导航到入口。",
      "data": {
        "images": [
          "http://pic.ezparking.com.cn/rtpi-service/parking?key=geztypqwhewtm1ztzcc0axpru6eo4rtq\u0026type=photo\u0026id=8eFNJKjl\u0026file=entrance_ZqMGYnoa.jpg",
          "http://pic.ezparking.com.cn/rtpi-service/parking?key=geztypqwhewtm1ztzcc0axpru6eo4rtq\u0026type=photo\u0026id=8eFNJKjl\u0026file=building_Yg90HemE.jpg",
          "http://pic.ezparking.com.cn/rtpi-service/parking?key=geztypqwhewtm1ztzcc0axpru6eo4rtq\u0026type=photo\u0026id=8eFNJKjl\u0026file=entrance_ZqMGYnoa.jpg",
          "http://pic.ezparking.com.cn/rtpi-service/parking?key=geztypqwhewtm1ztzcc0axpru6eo4rtq\u0026type=photo\u0026id=8eFNJKjl\u0026file=exit_oFkE3v2G.jpg"
        ]
      }
    }
  ]
```

---

### \/Available
还有车位吗

_举例：数据部分_
```
   "results": [
    {
      "hint": "目前该停车场车位充足，推荐在此停车"
    }
  ]
```

---

### \/HowToPay
可以用哪些支付方式

_举例：数据部分_
```
  "results": [
    {
      "hint": "该停车场支持现金"
    }
  ]
```

---

### \/ Resume
继续播放

_举例：数据部分_
```
   "results": [
      {
         "hint": "请欣赏 腾讯科技 腾讯科技 手握4000亿现金 中国移动是否能够大象起舞",
         "data": {
            "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b6d7568f4.mp3",
            "timestamp": 1517467353,
            "tagTopic": "科技",
            "name": "腾讯科技 手握4000亿现金 中国移动是否能够大象起舞"
         },
         "formatType": "audio"
      }
   ]
```

---

### \/Replay
指重播当前新闻（1遍）

_举例：数据部分_

```
    "results": [
       {
	"hint": "为您播放 高明 油价上涨助推欧元区通胀超预期 欧央行宽松压力加大",
	"data": {
		"audio": "http://mp3.tingwen.me/data/upload/mp3/5a728f0d1fb09.mp3",
		"timestamp": 1517457169,
		"tagTopic": "财经",
		"name": "油价上涨助推欧元区通胀超预期 欧央行宽松压力加大"
	},
	"formatType": "audio"
       }
    ]
```

---

### \/Exit
退出新闻场景


# 3.槽位

| **Slot\_Key** | **Description** | **Main\_Description** | **Example** |
| --- | --- | --- | --- |
| tag_topic | 新闻主题 | 用于指定新闻主题 | 财经,科技 |
| keywords | 关键字 | 用于指定人物，事件，话题，地区等 | 刘德华 余额宝 爆炸 |
| category | 新闻类别 | 已经播放过摘要，需要再次收听时，需指明 | 摘要 快报 |
| type | 场景类型 | 进入此场景，全部为新闻 | 新闻 资讯 |

# 4.返回字段描述

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | string | 提示语 | 请欣赏 听闻下午茶 听闻下午茶 软银集团和共享办公空间公司WeWork在日本成立合资公司 |
| data |  |  |  |  |
|  | audio | string | 新闻播放地址 | http://mp3.tingwen.me/data/upload/mp3/596e2a9d01ae2.mp3 |
|  | name | string | 新闻标题 | 软银集团和共享办公空间公司WeWork在日本成立合资公司 |
|  | tagTopic | string | 新闻主题 | 财经 |
|  | timestamp | int | 新闻产生时间戳 | 1502364363 |
| formatType |  | string | 结果类型 | audio |
