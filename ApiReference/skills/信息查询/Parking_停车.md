
# 1. 服务简介

停车服务，查询附近的停车场信息，查询车位情况\/收费信息

# 2.意图

### \/Search

查询附近的停车场信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;lot_count&gt; | 查找附近的三个停车场 |
| &lt;keywords&gt; | 我想听九寨沟的新闻 |
| &lt;category&gt; | 我想听新闻摘要 |
| &lt;type&gt; | 我想听新闻 |

_举例：数据部分_
```
我想听新闻
  "results": [
      {
         "hint": "我们一起听 听闻早餐 听闻早餐 微信新功能 支持双账号登录 2018年2月1日",
         "data": {
            "audio": "http://mp3.tingwen.me/data/upload/mp3/5a724f902a574.mp3",
            "timestamp": 1517440923,
            "tagTopic": "政治",
            "name": "听闻早餐 微信新功能 支持双账号登录 2018年2月1日"
         },
         "formatType": "audio"
      }
   ]
   
下一批
   "results": [
   {
      "hint": "请欣赏 飞碟说 飞碟说 误会大了 考古才不是持证盗墓",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72ba02a1741.mp3",
         "timestamp": 1517468173,
         "tagTopic": "",
         "name": "飞碟说 误会大了 考古才不是持证盗墓"
      },
      "formatType": "audio"
   }, {
      "hint": "我们一起听 笔记侠快播 笔记侠快播 不要被新零售迷惑",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b80dc6f38.mp3",
         "timestamp": 1517467669,
         "tagTopic": "财经",
         "name": "笔记侠快播 不要被新零售迷惑"
      },
      "formatType": "audio"
   }, {
      "hint": "为您播放 艾问人物 艾问人物 坎普拉德 离世的宜家创始人如何从卖火柴逆袭成隐形首富",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b7c7784bc.mp3",
         "timestamp": 1517467596,
         "tagTopic": "财经",
         "name": "艾问人物 坎普拉德 离世的宜家创始人如何从卖火柴逆袭成隐形首富"
      },
      "formatType": "audio"
   }, {
      "hint": "为您播放 互联网新鲜事 互联网新鲜事 今日头条宣战百度",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b7078944f.mp3",
         "timestamp": 1517467539,
         "tagTopic": "科技",
         "name": "互联网新鲜事 今日头条宣战百度"
      },
      "formatType": "audio"
   }, {
      "hint": "请欣赏 腾讯科技 腾讯科技 手握4000亿现金 中国移动是否能够大象起舞",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b6d7568f4.mp3",
         "timestamp": 1517467353,
         "tagTopic": "科技",
         "name": "腾讯科技 手握4000亿现金 中国移动是否能够大象起舞"
      },
      "formatType": "audio"
   }, {
      "hint": "我们一起听 无冕财经 无冕财经  一条 抱京东大腿是站队吗",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b69358b31.mp3",
         "timestamp": 1517467286,
         "tagTopic": "财经",
         "name": "无冕财经  一条 抱京东大腿是站队吗"
      },
      "formatType": "audio"
   }, {
      "hint": "请欣赏 听闻下午茶 听闻下午茶 2018丝路春晚全明星阵容曝光 看那些记忆中的 传奇 集体现身 2018年2月1日",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b42026ab4.mp3",
         "timestamp": 1517466690,
         "tagTopic": "政治",
         "name": "听闻下午茶 2018丝路春晚全明星阵容曝光 看那些记忆中的 传奇 集体现身 2018年2月1日"
      },
      "formatType": "audio"
   }, {
      "hint": "为您播放 高明 \"贾跃亭的乐视时代\"结束 因为他爆仓了",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a728ff4a0128.mp3",
         "timestamp": 1517457401,
         "tagTopic": "财经",
         "name": "\"贾跃亭的乐视时代\"结束 因为他爆仓了"
      },
      "formatType": "audio"
   }, {
      "hint": "为您播放 高明 日方抗议日企因\"问题地图\"被罚 外交部:应遵守法律",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a728f66d717f.mp3",
         "timestamp": 1517457257,
         "tagTopic": "政治",
         "name": "日方抗议日企因\"问题地图\"被罚 外交部:应遵守法律"
      },
      "formatType": "audio"
   }, {
      "hint": "我们一起听 高明 台商批当局阻两岸航班遭打压:不许为大陆说话",
      "data": {
         "audio": "http://mp3.tingwen.me/data/upload/mp3/5a728f360903b.mp3",
         "timestamp": 1517457210,
         "tagTopic": "政治",
         "name": "台商批当局阻两岸航班遭打压:不许为大陆说话"
      },
      "formatType": "audio"
   }
   ]
```

---


### \/Next
下一个

_举例：数据部分_
```
   "results": [
      {
         "hint": "为您播放 笔记侠快播 笔记侠快播 不要被新零售迷惑",
         "data": {
            "audio": "http://mp3.tingwen.me/data/upload/mp3/5a72b80dc6f38.mp3",
            "timestamp": 1517467669,
            "tagTopic": "财经",
            "name": "笔记侠快播 不要被新零售迷惑"
         },
         "formatType": "audio"
      }
   ]
```

---

### \/Prev
上一个

_举例：数据部分_
```
    "results": [
       {
	  "hint": "请欣赏 飞碟说 飞碟说 误会大了 考古才不是持证盗墓",
	  "data": {
		"audio": "http://mp3.tingwen.me/data/upload/mp3/5a72ba02a1741.mp3",
		"timestamp": 1517468173,
		"tagTopic": "",
		"name": "飞碟说 误会大了 考古才不是持证盗墓"
	  },
	  "formatType": "audio"
       } 
    ]
```

---

### \/Pause
暂停

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
