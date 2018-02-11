
# 1. 服务简介

停车服务，查询附近的停车场信息，查询车位情况\/收费信息

# 2.意图

### \/Search

查询附近的停车场信息

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;lot_count&gt; | 查找附近的三个停车场 |
| &lt;spec_dst&gt; | 查找目的地附近的停车场 |
| &lt;nth&gt; | 查看第二个 |

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

### \/ GetFee
停车多少钱

_举例：数据部分_
```
  "results": [
    {
      "hint": "双休日标准收费: 07:00-21:00 0.5元/15分钟,21:00-07:00 1元/2小时"
    }
  ]
```

---

### \/Navigate
导航到这里

_举例：数据部分_

```
  "results": [
    {
      "hint": "好的，即将为你导航到北科创业大厦地面停车场",
      "data": {
        "coordinate": {
          "latitude": 40.039867,
          "longitude": 116.41554
        }
      }
    }
  ]
```

---


# 3.槽位

| **Slot\_Key** | **Description** | **Main\_Description** | **Example** |
| --- | --- | --- | --- |
| lot_count | 停车场个数 | 用于指定查找停车场的个数 | 三个 |
| spec_dst | 目的地 | 用于指定查找目的地附近的停车场 | 目的地 |
| nth | 第几个 | 用于指定查看第几个停车场详情 | 第二个 |

# 4.返回字段描述

| **Field\_Name** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- |
| hint |  | string | 提示语 | 北科创业大厦地面停车场为完全对外开放地面停车场...... |
| data |  |  |  |  |
|  | images | []string | 停车场入口图片 | ["http://pic.ezparking.com.cn/rtpi-......", ".......=building_Yg90HemE.jpg"] |


| **Field\_Name** | **Sub\_Field** | **Sub\_Field** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- | --- | --- |
| hint |  |  | string | 提示语 | 北科创业大厦地面停车场为完全对外开放地面停车场...... |
| data |  |  |  |  |  |
|  | coordinate |  |  |  |  |
|  |  | latitude | float64 | 纬度 | 40.039867 |
|  |  | longitude | float64 | 经度 | 116.41554 |
