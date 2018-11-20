# 1.技能简介

PoiNavigation 包含语音地图控制和POI的导航服务，用户可以导航到位置或者其周边的POI信息，如餐厅，酒店，加油站，医院，停车场等也可以语音控制地图，如：放大/缩小地图，打开/关闭路况，高速优先，搜索技术由高德地图提供。

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

note: 不带location但是request里包含经纬度信息时，以当前经纬度查询poi信息

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



<tr>

   <td >NaviToAroundName</td>

   <td >导航到附近的POI名称</td>

   <td>a.导航到周边的便利蜂</br>b.导航到附近的物美超市</td>
   
   <td>无</td>
 
</tr>

<tr>

   <td >NaviToCategory</td>

   <td >导航到POI分类</td>

   <td>a.导航到朝阳区酒店</br>b.导航到海淀区超市</td>
   
   <td>无</td>
 
</tr>

<tr>

   <td >NaviToAroundCategory</td>

   <td >导航到附近的POI分类</td>

   <td>a.导航到周边的酒店</br>b.导航到附近的超市</td>
   
   <td>无</td>
 
</tr>

<tr>

   <td >NaviWithPassby</td>
 
   <td >NaviWithPassby</td>

   <td >途经点导航</br>（最多支持三个点）</td>

   <td>a.先去途中的鸟巢<br>b.先导航去鸟巢再去天安门<br>c.先导航去鸟巢再去天安门最后去立水桥南</td>
   
   <td>无</td>
   

</tr>


<tr>

   <td rowspan="2">SetAlias</td>
 
   <td >SetAliasAddressByName</td>

   <td >设置别名地址为指定的POI名称</td>

   <td>a.把家里的地址设置为立水桥南</br>把银河SOHO设置为公司的地址</td>
   
   <td>alias</td>
   
  <td rowspan="24">上文：navi</br>下文：navi</td>

</tr>

<tr>
 
   <td >setAliasAddressByCurrent</td>

   <td >设置别名地址为当前地址</td>

   <td>a.把家里的地址设置为当前位置</br>把当前位置设置为公司的地址</td>
   
   <td>alias</td>
   
</tr>

<tr>

   <td >NaviToAlias</td>
 
   <td >NaviToAlias</td>

   <td >导航到地址别名</td>

   <td>a.导航回家</br>b.导航去上班</td>
   
   <td>alias</td>

</tr>

<tr>

   <td >Select</td>
 
   <td >Select</td>

   <td >索引选择</td>

   <td>a.第一个</br>第二个</td>
   
   <td>number</td>
   
</tr>



<tr>

   <td >ChangeCompass</td>
 
   <td >ChangeCompass</td>

   <td >指北针模式切换</td>

   <td>a.车头向上模式</br>b.设置为指北模式</td>
   
   <td>compass_mode</td>
   
</tr>

<tr>

   <td >OpenRoute</td>
 
   <td >OpenRoute</td>

   <td >打开路线模式</td>

   <td>a.设定为高速优先</br>b.切换成避免收费</td>
   
   <td>route_mode</td>

</tr>

<tr>

   <td >CloseRoute</td>
 
   <td >CloseRoute</td>

   <td >关闭路线模式</td>

   <td>a.关闭躲避拥堵</br>b.关闭高速优先</td>
   
   <td>route_mode</td>

</tr>
<tr>

   <td >OpenFullView</td>
 
   <td >OpenFullView</td>

   <td >打开全程模式</td>

   <td>查看全览模式</td>
   
   <td>无</td>

</tr>

<tr>

   <td >CloseFullView</td>
 
   <td >CloseFullView</td>

   <td >关闭全程模式</td>

   <td>关闭全程模式</td>
   
   <td>无</td>

</tr>
<tr>

   <td >AskRemainTime</td>
 
   <td >AskRemainTime</td>

   <td >查询导航剩余时间</td>

   <td>a.还有多久能到</br>b.目的地还要多长时间</td>
   
   <td>无</td>

</tr>

<tr>

   <td >AskArrivalTime</td>
 
   <td >AskArrivalTime</td>

   <td >查询预计到达时间</td>

   <td>a.几点能到<br>b.什么时候能到</td>
   
   <td>无</td>

</tr>

<tr>

   <td >AskRemainDistance</td>
 
   <td >AskRemainDistance</td>

   <td >查询导航剩余距离</td>

   <td>a.还有多少公里</br>还有几公里</td>
   
   <td>无</td>

</tr>

<tr>

   <td >AskCurrentRoad</td>
 
   <td >AskCurrentRoad</td>

   <td >查询当前道路</td>

   <td>a.当前道路</br>我现在在哪条路上</td>
   
   <td>无</td>

</tr>

<tr>

   <td >OpenRCondi</td>
 
   <td >OpenRCondi</td>

   <td >查看路况</td>

   <td>a.开启路况</br>查看路况</td>
   
   <td>无</td>

</tr>

<tr>

   <td >CloseRCondi</td>
 
   <td >CloseRCondi</td>

   <td >关闭路况</td>

   <td>a.关掉路况</br>关闭路况</td>
   
   <td>无</td>

</tr>

<tr>

   <td >ZoomInMap</td>
 
   <td >ZoomInMap</td>

   <td >放大地图</td>

   <td>a.放大地图</br>调大一点地图</td>
   
   <td>无</td>

</tr>

<tr>

   <td >ZoomOutMap</td>
 
   <td >ZoomOutMap</td>

   <td >缩小地图</td>

   <td>a.缩小地图</br>调小一点地图</td>
   
   <td>无</td>

</tr>

<tr>

   <td >OpenBroadcast</td>
 
   <td >OpenBroadcast</td>

   <td >打开导航语音</td>

   <td>a.打开导航语音</br>打开导航语音播报</td>
   
   <td>无</td>

</tr>

<tr>

   <td >CloseBroadcast</td>
 
   <td >CloseBroadcast</td>

   <td >关闭导航语音</td>

   <td>a.关闭导航语音</br>关闭导航语音播报</td>
   
   <td>无</td>

</tr>

<tr>

   <td >Continue</td>
 
   <td >Continue</td>

   <td >继续导航</td>

   <td>a.继续导航</br>接着导航</td>
   
   <td>无</td>

</tr>

<tr>

   <td >Exit</td>
 
   <td >Exit</td>

   <td >退出导航</td>

   <td>a.退出导航</td>
   
   <td>无</td>

</tr>

</table>

# 5.返回字段说明

| **result** | **Description** | **value** | **type** |**Required** |
| ------------ | ------------ | ------------ | ------------ |------------ |
| id | poi的ID | amap-B000A7OUR9 | string |Required|
| name | poi的名称 | 东城社区卫生服务站(小牌坊胡同) | string |Required|
| tel | 电话号码 | 010-85111691 | string |Optional|
| type | poi地点的类型 | 医疗保健服务;综合医院;卫生院 | string |Optional|
| passByIndex |途经点 （1 2 3 代表第X个途径点） | 1 | string |Optional|
| distance | 距离该poi点的直线距离，单位：米 | 183 | string |Optional|
| location | poi名称对应的经纬度信息 | [详情查阅](/Bot/3-ApiReference/rosai-client-development-protocol-intent.md#23-location-定义) | string|Optional|



# 6.语义测试
运行语义测试前请确保：

1.拥有ros.ai 开发平台账号

2.确认该账号下要测试的场景已经打开

[语意测试连接](https://passport.ros.ai/#/login)





