# 1. 服务简介

用户可以询问指定位置或者其周边的POI信息，如餐厅，酒店，加油站，医院，停车场等。搜索服务由高德地图提供。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| strong_name | 强实体名称 | 国贸大厦、鸟巢 |
| any_name | 任意名称匹配项 | 鸟巢123停车场，中的 ‘123’ |
| center_strong_name | 周边搜索时中心，强点实体名称 | 鸟巢123停车场，中的‘鸟巢’ |
| center_any_name | 周边搜索时中心，任意名称匹配项 | 123附近的停车场，中的‘123’ |
| hotspot | 热门地点实体名称 | 中关村、国贸 |
| province | 地址所在的省份名| 省份：河北、广东 城市：邢台、佛山 | 
| city | 地址所在的城市名 | 北京市 |
| district | 地址所在的区 | 朝阳区|
| category | poi分类 | 酒店、医院、停车场|
| radius | 搜索范围 | 500米、1千米、2公里|
| radius_unit | 搜索范围的单位 | 米、千米、公里|

# 3.意图

note: 不带location但是request里包含经纬度信息时，以当前经纬度查询poi信息

| **Semantic** | **Description** | **Example** |
| --- | --- | --- |
| SearchHotspotByName | 查找热门地点+名称 | 国贸的便利蜂 、国贸的手机店|
| SearchAroundByName | 查找周边的POI名称 | 查找周边的便利蜂、附近的物美超市 |
| SearchByName | 查找POI名称 | 儿研所在哪、北京市的711 |
| SearchHotspotByCategory | 查找热门地点+名称 | 国贸的加油站 、国贸的酒店 |
| SearchAroundByCategory | 查找周边的POI分类 | 附近的餐厅 、附近的酒店|
| SearchByCategory| 查找POI分类 | 哪里有酒店、哪里有医院 |

# 4.返回字段说明

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint|  |  | 提示语：为您找到以下结果 | string |
| emotions |||
|  | type || string | 
|  | level || int | 
|  | code || string | 
| data ||| 
|  | address | 具体地址：朝阳门街道小牌坊胡同30号 | string | 
|  | adname | 所在的地区：东城区 | string | 
|  | cityname | 所在城市：北京市 | string | 
|  | distance | 直线距离：183 单位同意为 ‘米’ | string | 
|  | id | poi的ID：amap-B000A7OUR9 | string | 
|  | location | poi名称对应的经纬度信息：116.432986,39.919049 | string | 
|  | name | poi的名称：东城社区卫生服务站(小牌坊胡同) | string | 
|  | pname | 地址所在的省份名：北京市 | string | 
|  | tel | 电话号码：010-85111691 | string | 
|  | type | poi地点的类型：医疗保健服务;综合医院;卫生院 | string | 

### 返回样例
```json
{
    <!--  忽略其他 -->
    "results":[
        {
            "hint":"为您找到以下结果",
            "emotions":[
                {
                    "type":"answer",
                    "level":0,
                    "code":"A001"
                }
            ],
            "data":[
                {
                    "address":"朝阳门街道小牌坊胡同30号",
                    "adname":"东城区",
                    "cityname":"北京市",
                    "distance":"183",
                    "id":"amap-B000A7OUR9",
                    "location":"116.432986,39.919049",
                    "name":"东城社区卫生服务站(小牌坊胡同)",
                    "pname":"北京市",
                    "tel":"010-85111691",
                    "type":"医疗保健服务;综合医院;卫生院"
                }
            ]
        }
    ]
}
```
