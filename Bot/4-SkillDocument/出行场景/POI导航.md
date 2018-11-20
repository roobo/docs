# 1.技能简介

PoiNavigation 保护语音地图控制和POI的导航服务，用户可以导航到位置或者其周边的POI信息，如餐厅，酒店，加油站，医院，停车场等也可以语音控制地图，如：放大/缩小地图，打开/关闭路况，高速优先，搜索技术由高德地图提供。

# 2.场景安装指导

一个场景无法保证适用于所有产品，这里会列举出一些我们的场景接入建议，帮助用户做出决策。

| **Product** | **Recommend** | **Description** |
| ------------ | ------------ | ------------ |
| 无屏设备 | 否 |  仅靠 outputSpeech完成交互体验较差，期望有UI配合展示 [详情查阅](/Bot/4-SkillDocument/最佳实践.md) |

# 3.返回槽位说明

技能平台分析过后会产生槽位信息，此处是该技能返回的槽位的集合，槽位名一致时槽位意义相同，不区分意图。

| **Slot** | **Description** | **Example** |**Value** | **Type** |
| ------------ | ------------ | ------------ | ------------ | ------- |
| alias | 地址别名 | a.导航回家</br>b.导航去上班 | a.Home</br>b.Company | String |
| number | 选项索引 | 第一个 | 1 | String |
| route_mode | 路线模式 | a.关闭躲避拥堵</br>b.设定为高速优先</br>c.切换成避免收费</br>d.选择不走高速 | a.AvoidCongestion</br>b.Highway</br>c.NoCharge</br>d.NoHighway | String |
| compass_mode | 地图/车头朝向模式 | a.车头向上模式</br>b.设置为指北模式 | a.HeadUp</br>b.NorthUp | String |

# 4.返回意图说明


罗列出了该技能的意图和子意图描述信息，每一个意图所支持的槽位信息，及会确保会进到该意图的示例，可以根据给出的示例到测试接口去得到最终的返回数据。

<table>

<tr>

<td><b>Intent</b></td>

<td><b>SubIntent</b></td>

<td><b>Description</b></td>

<td><b>Example</b></td>

<td><b>Slot</b></td>

</tr>

<tr>

<td rowspan="2">Search</td>

  <td >NaviToName</td>

   <td >导航到POI名称</td>

   <td>导航到鸟巢</br>导航到的物美超市</td>
   
   <td>无</td>


</tr>



<tr>

   <td >NaviToName</td>

   <td >导航到POI名称</td>

   <td>查找周边的便利蜂、附近的物美超市</td>
   
   <td>无</td>

</tr>

</table>









