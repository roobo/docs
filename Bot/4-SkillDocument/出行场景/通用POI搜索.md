# 1. 技能简介

PublicPOI 查地标,用户可以询问指定位置或者其周边的POI信息，如餐厅，酒店，加油站，医院，停车场等。搜索技术由高德地图提供。

# 2.技能安装指导

一个技能无法保证适用于所有产品，这里会列举出一些我们的场景接入建议，帮助用户做出决策。

| **Product** | **Recommend** | **Description** |
| ------------ | ------------ | ------------ |
| 无屏设备 | 否 |  仅靠 outputSpeech完成交互体验较差，期望有UI配合展示 [详情查阅](/Bot/4-SkillDocument/最佳实践.md) |


# 3.返回槽位说明

无

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
        <td rowspan="6">Search</td>    
        <td >SearchHotspotByName</td>  
       <td >查找热门地点+名称</td>  
       <td >国贸的便利蜂 、国贸的手机店</td> 
       <td>无</td>
       <td>无</td>
    </tr>
   <tr>
        <td >SearchAroundByName</td>  
       <td >查找周边的POI名称</td>  
       <td >查找周边的便利蜂、附近的物美超市</td> 
       <td>无</td>
       <td>无</td>
   </tr>
   <tr>
        <td >SearchByName</td>  
       <td >查找POI名称</td>  
       <td >儿研所在哪、北京市的711</td> 
       <td>无</td>
       <td>无</td>
   </tr>
     <tr>
        <td >SearchHotspotByCategory</td>  
       <td >查找热门地点+名称</td>  
       <td >国贸的加油站 、国贸的酒店</td> 
       <td>无</td>
       <td>无</td>
   </tr>
        <tr>
        <td >SearchAroundByCategory</td>  
       <td >查查找周边的POI分类</td>  
       <td >附近的餐厅 、附近的酒店</td> 
       <td>无</td>
       <td>无</td>
   </tr>
   <tr>
        <td >SearchByCategory</td>  
       <td >查找POI分类</td>  
       <td >哪里有酒店、哪里有医院</td> 
       <td>无</td>
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
| distance | 距离该poi点的直线距离，单位：米 | 183 | string |Optional|
| location | poi名称对应的经纬度信息 | [详情查阅](/Bot/3-ApiReference/rosai-client-development-protocol-intent.md#23-location-定义) | string|Optional|




# 6.语义测试
运行语义测试前请确保：

1.拥有ros.ai 开发平台账号

2.确认该账号下要测试的场景已经打开

[语意测试连接](https://passport.ros.ai/#/login)

