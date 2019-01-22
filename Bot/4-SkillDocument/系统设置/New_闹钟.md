
# 1.技能简介
Clock(闹钟) , 可以帮用户设置闹钟和提醒。

# 2.技能安装指导

一个技能无法保证适用于所有产品，这里会列举出一些我们的场景接入建议，帮助用户做出决策。

| **Product** | **Recommend** | **Description** |
| ------------ | ------------ | ------------ |
| 无屏设备 | 否 |  仅靠 outputSpeech完成交互体验较差，期望有UI配合展示 [详情查阅](/Bot/4-SkillDocument/最佳实践.md) |

# 3.返回槽位说明
| **Slot** | **Description** | **Example** |**Value** | **Type** |
| ------------ | ------------ | ------------ | ------------ | ------- |
| num | 选项数字 | a.第一个| a.1 | String |
| content | 提醒时的内容 | a.中午12点叫我吃饭| a.吃饭 | String |
| date_time | 日期时间 | a.今天10点叫我起床</br>b.2019年1月24日10点叫我起床</br>c.过5分钟以后准时叫我 | a.{\"date\":\"2019-01-22\",\"time\":\"10:00:00\",\"meridian\":\"\",\"illegal\":0}<br>b.{\"date\":\"2019-01-24\",\"time\":\"10:00:00\",\"meridian\":\"\",\"illegal\":0}</br>c.{\"date\":\"2019-01-22\",\"time\":\"11:35:43\",\"meridian\":\"am\",\"illegal\":0} | Map |
| time_repeat | 可重复的日期时间 | a.每天下午1点叫我起床</br> | a.{\"date\":\"1,2,3,4,5,6,7 每天\",\"time\":\"01:00:00\",\"meridian\":\"pm\",\"illegal\":0} | Map |
| time_period | 时间段， 上/下午等 | a.今天下午叫我起床<br>b.晚上叫我起床| a.下午</br>b.晚上 | String |
| data | 日期 | a.今天下午叫我起床<br>b.明天下午叫我起床| a.2019-01-22</br>b.2019-01-23 | String |
| alarm_repeat | 闹钟提醒，周期类型 | a.每天下午叫我起床<br>b.工作日下午叫我起床| a.每天</br>b.工作日 | String |
| date_repeat | 闹钟提醒，周期类型 | a.每周一叫我起床<br>b.每个工作日叫我起床| a.1 每周一</br>b.1,2,3,4,5 每个工作日 | String |
| duration | 日期段 | a.未来三天13点叫我起床| a.2019-01-23/2019-01-25 | String |
| date_time_from | 日期时间与date_time内容一致 | 14点的闹钟修为15点| a.{\"date\":\"\",\"time\":\"02:00:00\",\"meridian\":\"pm\",\"illegal\":0} | Map |
| date_time_to | 日期时间与date_time内容一致 | 14点的闹钟修为15点| a.{\"date\":\"\",\"time\":\"03:00:00\",\"meridian\":\"pm\",\"illegal\":0} | Map |
| time_repeat_from | 可重复的日期时间与time_repeat内容一致 | a.每天下午一点的闹钟修改为每天下午两点</br> | a.{\"date\":\"1,2,3,4,5,6,7 每天\",\"time\":\"01:00:00\",\"meridian\":\"pm\",\"illegal\":0} | Map |
| time_repeat_to | 可重复的日期时间与time_repeat内容一致 | a.每天下午一点的闹钟修改为每天下午两点</br> | a.{\"date\":\"1,2,3,4,5,6,7 每天\",\"time\":\"02:00:00\",\"meridian\":\"pm\",\"illegal\":0} | Map |

# 4.返回意图说明


<table>

<tr>

<td><b>Intent</b></td>

<td><b>SubIntent</b></td>

<td><b>Description</b></td>

<td><b>Example</b></td>

<td><b>Slot</b></td>

<td><b>Context</b></td>

</tr>

<tr>

<td rowspan="4">Navigate</td>

  <td >NaviToName</td>

   <td >导航到POI名称</td>

   <td>a.导航到鸟巢</br>b.导航到的物美超市</td>
   
   <td>无</td>
   
 <td rowspan="5">上文：navi</br>下文：navi</td>

</tr>

