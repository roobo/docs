
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
| date | 日期 | a.今天下午叫我起床<br>b.明天下午叫我起床| a.2019-01-22</br>b.2019-01-23 | String |
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

<td rowspan="3">SetClock</td>

  <td >SetClock</td>

   <td >添加闹钟</td>

   <td>a.10分钟以后叫我起床</br>b.明天早上6点叫我起床</td>
   
   <td rowspan="3">date</br>time_repeat</br>time_period</br>duration</br>date_time</br>date_repeat</br>alarm_repeat
   
 <td>无</td>
</tr>
<tr>
<td >SetClockBegin</td>

   <td >添加闹钟指定部分条件参数</td>

   <td>a.明天早叫我起床</br>b.下午叫醒我</td>
   
 <td>上文：无 下文：ask_clock</td>

</tr>

<tr>
<td >SetClockSlotSupplement</td>

   <td >添加闹钟条件补充</td>

   <td>a.下午3点</td>
   
 <td>上文：ask_clock  下文：无</td>

</tr>

<tr>

<td rowspan="4">SetAlarm</td>

  <td >SetAlarm</td>

   <td >添加事件提醒</td>

   <td>a.10分钟以后提醒喝水</br>b.明天早上6点提醒我吃早茶</td>
   
   <td rowspan="4">date</br>time_repeat</br>time_period</br>duration</br>date_time</br>date_repeat</br>alarm_repeat</br>content</td>
   
 <td>无</td>
</tr>

<tr>
<td >SetAlarmBegin</td>

   <td >添加事件提醒指定部分条件</td>

   <td>a.提醒我</br>明天提醒我</td>
   
 <td>上文：  下文：ask_alarm_time</td>

</tr>

<tr>
<td >SetAlarmByTime</td>

   <td >添加事件提醒，指定部分条件</td>

   <td>a.10分钟以后提醒我</br>b.明天早上6点提醒我</td>
   
 <td>上文：  下文：ask_content</td>

</tr>
<tr>
<td >SetAlarmSlotSupplement</td>

   <td >添加事件提醒，添加补充</td>

   <td>a.6点</br> b.吃饭</td>
   
 <td>上文：ask_alarm_time,ask_content  下文：无</td>

</tr>

<tr>

<td rowspan="5">UpdateClock</td>

  <td >UpdateClock</td>

   <td >更新闹钟提醒</td>

   <td>a.14点的闹钟修改为16点</td>
   
   <td rowspan="5">date</br>num</br>time_repeat</br>date_time</br>time_repeat</br>date_time_from</br>date_time_to</br>alarm_repeat</br>time_repeat_from</br>time_repeat_to</td>
   
 <td>无</td>
</tr>

<tr>
<td >UpdateClockBegin</td>

   <td >更新闹钟提醒，不指定条件</td>

   <td>a.修改闹钟</td>
   
 <td>上文：无  下文：ask_num</td>

</tr>

<tr>
<td >UpdateClockBeginByFromTime</td>

   <td >更新闹钟提醒，指定存在的闹钟时间</td>

   <td>a.修改16点的闹钟</td>
   
 <td>上文：无  下文：ask_to</td>

</tr>

<tr>
<td >UpdateClockBeginByToTime</td>

   <td >更新闹钟提醒，指定修改后的时间</td>

   <td>a.闹钟修改为17点</td>
   
 <td>上文：无  下文：ask_from</td>

</tr>

<tr>
<td >UpdateClockSlotSupplement</td>

   <td >更新闹钟提醒，条件补充</td>

   <td>a.第一个</br>b.17点那个</br>下午6点</td>
   
 <td>上文：ask_num,ask_from,ask_to  下文：无</td>

</tr>

<tr>

<td rowspan="3">DeleteClock</td>

  <td >DeleteClock</td>

   <td >删除闹钟</td>

   <td>a.删除14点的闹钟</br>b.删除今天的闹钟</td>
   
   <td rowspan="3">date</br>num</br>time_repeat</br>date_time</br>time_repeat</br>duration</td>
   
 <td>无</td>
 </tr>
 
 <tr>
<td >DeleteClockBegin</td>

   <td >删除闹钟</td>

   <td>a.删除闹钟</br>b.我要删除闹钟</td>
   
 <td>上文：无  下文：ask_del</td>

</tr>

 <tr>
<td >DeleteClockSlotSupplement</td>

   <td >闹钟信息补充</td>

   <td>a.第一个</br>b.17点那个</td>
   
 <td>上文：无  下文：ask_del</td>

</tr>
 
<tr>

<td rowspan="1">GetClock</td>

  <td >GetClock</td>

   <td >查询闹钟</td>

   <td>a.查询闹钟</br>b.查询今天的闹钟</td>
   
   <td rowspan="1">date</br>date_time</br>time_period</td>
   
 <td>无</td>
 </tr>
 
 <tr>

<td rowspan="1">GetClock</td>

  <td >DelayClock</td>

   <td >延迟响铃</td>

   <td>a.等下再叫我</br>b.5分钟以后记得再叫我</td>
   
   <td rowspan="1">date_time</td>
   
 <td>无</td>
 </tr>
 
  <tr>

<td rowspan="1">StopClock</td>

  <td >StopClock</td>

   <td >停止响铃</td>

   <td>a.布丁布丁 </br>b.别闹了</td>
   
   <td rowspan="1">无</td>
   
 <td>上：clock_ring 下：无</td>
 </tr>
 
 </tr>
</table>
  
  
 
 
 # 5.返回字段说明

| **result** | **Description** | **value** | **type** |**Required** |
| ------------ | ------------ | ------------ | ------------ |------------ |
| id | 闹钟的id | 8581 | int |Required|
| alarm_time | 闹钟的时间 | 2019-01-22 18:00:00 | string |Required|
| content | 时间提醒内容（闹钟时该字段为空） | 吃饭 | string |Optional|
| operation | 操作项 set为新增</br>list为列表/br>delete为删除/br>update为修改</br>hibernate为定时休眠</br>cancelHibernate取消定时休眠| 医疗保健服务;综合医院;卫生院 | string |Optional|
| repeat_mode |提醒模式，为0表示特定时刻闹钟，非0表示重复闹钟，按日提醒格式从左到右为</br>（预留 周一 周二 周三 周四 周五 周六 周日），例如00100000代表的数字是32，代表每周二 | 1 | int |Required|



# 6.语义测试
运行语义测试前请确保：

1.拥有ros.ai 开发平台账号

2.确认该账号下要测试的场景已经打开

[语意测试连接](https://passport.ros.ai/#/login)
 
 
