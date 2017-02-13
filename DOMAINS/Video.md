## Video

```
视频点播
```
* [Play](#Play)
* [Alter](#Alter)
* [Search](#Search)
* [Stop](#Stop)
* [Pause](#Pause)
* [Resume](#Resume)
* [FastForward](#FastForward)
* [FastBackward](#FastBackward)


#### Video: Play {#Play}

---

* _Data_

| Name | Data type | Required/Optional | Description | Request examples |
| :---: | :---: | :---: |:---: |:---: |
| category | string | optional | 视频分类 | 播放电影(category=电影) |
| mode | string | optional | 播放模式 | 循环播放勇敢的心(mode=循环) |
| actor | string | optional | 演员 | 播放靳东和陈乔恩主演的电视剧鬼吹灯(actor=靳东,陈乔恩) |
| director | string | optional | 导演 | 播放李安执导的电影(director=李安) |
| country | string | optional | 制片地区 | 播放港台电影(country=港台) |
| name | string | optional | 片名 | 放无间道看看(name=无间道) |
| popularity | string | optional | 评价 | 我要看热门评价高的电影(popularity=热门,好评) |
| tag | string | optional | 标签 | 播放恐怖的经典电影(tag=恐怖,经典) |
| datetime | string | optional | 日期 | 播放周星驰2008年的电影(datetime=2008--) |
| episode | string | optional | 季/集 | 播放破产姐妹第二季第一集(episode=2/1) |


* _datetime_ 时间格式
| Request examples | Response format |
| :---: | :---: |
| 2008年 | 2008-- |
| 2008年4月 | 2008-04- |
| 2008年4月15号 | 2008-04-15 |
| 4月 | 2017-04- |
| 4月15号 | 2017-04-15 |
| 八十年 | 1980--/1989-- |


* _episode_ 季/集格式
| Request examples | Response format |
| :---: | :---: |
| 第一季 | 1/ |
| 第一季第一集 | 1/1 |
| 倒数第一集 | /-1 |
| 最新一集 | /-1 |
| 第一季最新一集 | 1/-1 |
| 下一季 | ++1/ |
| 上一集 | /--1 |
| 上一季第一集 | --1/1 |


#### Video: Alter {#Alter}

---

#### Video: Search {#Search}

* _Data_

| Name | Data type | Required/Optional | Description | Request examples |
| :---: | :---: | :---: |:---: |:---: |
| category | string | optional | 视频分类 | 播放电影(category=电影) |
| mode | string | optional | 播放模式 | 循环播放勇敢的心(mode=循环) |
| actor | string | optional | 演员 | 播放靳东和陈乔恩主演的电视剧鬼吹灯(actor=靳东,陈乔恩) |
| director | string | optional | 导演 | 播放李安执导的电影(director=李安) |
| country | string | optional | 制片地区 | 播放港台电影(country=港台) |
| name | string | optional | 片名 | 放无间道看看(name=无间道) |
| popularity | string | optional | 评价 | 我要看热门评价高的电影(popularity=热门,好评) |
| tag | string | optional | 标签 | 播放恐怖的经典电影(tag=恐怖,经典) |
| datetime | string | optional | 日期 | 播放周星驰2008年的电影(datetime=2008--) |
| episode | string | optional | 季/集 | 播放破产姐妹第二季第一集(episode=2/1) |




#### Video: Stop {#Stop}

---

#### Video: Pause {#Pause}

---
#### Video: Resume {#Resume}

---
