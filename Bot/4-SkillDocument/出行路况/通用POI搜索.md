# 1. 服务简介

用户可以询问指定位置或者其周边的POI信息，如餐厅，酒店，加油站，医院，停车场等。搜索服务由高德地图提供。

# 2.意图

note: 不带location但是request里包含经纬度信息时，以当前经纬度查询poi信息

<table>
    <tr>
        <td>Intent</td> 
        <td>SubIntent</td> 
        <td>Description</td> 
        <td>Example</td> 
   </tr>
   <tr>
        <td rowspan="6">Search</td>    
        <td >SearchHotspotByName</td>  
       <td >查找热门地点+名称</td>  
       <td >国贸的便利蜂 、国贸的手机店</td> 
    </tr>
   <tr>
        <td >SearchAroundByName</td>  
       <td >查找周边的POI名称</td>  
       <td >查找周边的便利蜂、附近的物美超市</td> 
   </tr>
   <tr>
        <td >SearchByName</td>  
       <td >查找POI名称</td>  
       <td >儿研所在哪、北京市的711</td> 
   </tr>
     <tr>
        <td >SearchHotspotByCategory</td>  
       <td >查找热门地点+名称</td>  
       <td >国贸的加油站 、国贸的酒店</td> 
   </tr>
        <tr>
        <td >SearchAroundByCategory</td>  
       <td >查查找周边的POI分类</td>  
       <td >附近的餐厅 、附近的酒店</td> 
   </tr>
           <tr>
        <td >SearchByCategory</td>  
       <td >查找POI分类</td>  
       <td >哪里有酒店、哪里有医院</td> 
   </tr>
    
</table>


# 3.返回字段说明


| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint|  | 为您找到以下结果 | string |
| emotions |  | 情绪值定义 | |
| data | | | |
|  | address | 具体地址：朝阳门街道小牌坊胡同30号 | string | 
|  | adname | 所在的地区：东城区 | string | 
|  | cityname | 所在城市：北京市 | string | 
|  | distance | 直线距离：183 单位为 ‘米’ | string | 
|  | id | poi的ID：amap-B000A7OUR9 | string | 
|  | location | poi名称对应的经纬度信息：116.432986,39.919049 | string | 
|  | name | poi的名称：东城社区卫生服务站(小牌坊胡同) | string | 
|  | pname | 地址所在的省份名：北京市 | string | 
|  | tel | 电话号码：010-85111691 | string | 
|  | type | poi地点的类型：医疗保健服务;综合医院;卫生院 | string | 


### 返回样例

