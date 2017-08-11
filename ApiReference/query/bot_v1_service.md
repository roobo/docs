### /bot/v1/service

* [概述](#1-概述)
* [URLs](#2-URLs)
* [实例](#3-实例)

### 1 概述

---

服务开放接口，开发者在意图和参数已知的情况，无需再通过自然语言处理，可直接调用相应的服务接口。

### 2 URLs

---

| Method | Definition |
| :--- | :--- |
| POST /bot/v1/service/:domain/:method | :domain服务名; :method方法名。服务需要实现/bot/v1/service/:domain/:method。请求经过校验后会被转到这个地址。 |

### 3 实例

---

_Sample Request_

```
POST http://api.ros.ai/bot/v1/service/hotelbooking/list

Headers:
Content-Type: application/json; charset=utf-8

{
    "agentId": "2ZmNzYyOTA5MzJjZ",
    "token": "f7caaf310da3dcb24bacdc7944456210",
    "sessionId": "1234567890",
    "location": {
        "address": {
            "province": "北京",
            "detail": "丰台区",
            "city": "北京",
            "country": "中国"
        },
        "longitude": 0,
        "latitude": 0
    },
    "parameters": { ＃参数对象
        "hotel_name": "empty",
        "room_price": "200",
        "checkin_date": "2016-12-24",
        "checkout_date": "2016-12-26"
    }
}
```

_Sample Response_

```
{
    "status": {
        "code": 0,
        "errorType": "success"
    },
    "result": {
        "hint": "为您找到如下酒店",
        "data": [
            {
                "name": "7天连锁酒店（北京万丰路七里庄地铁站店）",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/433000/432029/86e3a250b2e3423e9825b32adabf8813_R_550_412.jpg",
                "price": 239,
                "type": "经济型",
                "recommend": "88%",
                "location": "丰台区七里庄",
                "distance": "距市中心约11公里"
            },
            {
                "name": "北京哈特商务酒店",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/49000/48660/CD5736E0-752E-46F1-BECF-17F34AF9C703_R_550_412.jpg",
                "price": 368,
                "type": "舒适型",
                "recommend": "80%",
                "location": "丰台区哈特商务酒店",
                "distance": "距市中心约7.6公里"
            },
            {
                "name": "北京林家公寓",
                "pic": "http://dimg04.c-ctrip.com/images/t1/hotel/1248000/1247897/057db9b24fa74c20b9b2891bc0ed4f87_R_550_412.jpg",
                "price": 100,
                "type": "经济型",
                "recommend": "20%",
                "location": "丰台区贵友商场",
                "distance": "距市中心约8.2公里"
            },
            {
                "name": "北京华苑饭店",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/644000/643646/fbb825e207404637bccc6a64532e9975_R_550_412.jpg",
                "price": 230,
                "type": "舒适型",
                "recommend": "82%",
                "location": "丰台区",
                "distance": "距市中心约13.6公里"
            },
            {
                "name": "北京燕岭宾馆",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/53000/52745/2B614ED0-1E8B-485F-ADC8-3FF3DC3A861B_R_550_412.jpg",
                "price": 388,
                "type": "舒适型",
                "recommend": "82%",
                "location": "丰台区燕岭宾馆餐厅",
                "distance": "距市中心约20.6公里"
            },
            {
                "name": "河南商务酒店",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/79000/78452/9104BA3C-87FF-495B-99CE-63BEADF6BBCC_R_550_412.jpg",
                "price": 398,
                "type": "舒适型",
                "recommend": "80%",
                "location": "丰台区汕头小吃",
                "distance": "距市中心约7.4公里"
            },
            {
                "name": "7天连锁酒店（北京莲石东路店）",
                "pic": "http://dimg04.c-ctrip.com/images/fd/hotel/g2/M06/13/E5/Cghzf1U0biuAcL-IAAHze3p0NVU875_R_550_412.jpg",
                "price": 250,
                "type": "经济型",
                "recommend": "88%",
                "location": "丰台区",
                "distance": "距市中心约14.9公里"
            },
            {
                "name": "北京豪都商务宾馆",
                "pic": "http://dimg04.c-ctrip.com/images/hotel/82000/81462/71ECA634-EA5A-4CAA-938A-CC3CE1A64E0F_R_550_412.jpg",
                "price": 278,
                "type": "舒适型",
                "recommend": "78%",
                "location": "丰台区实惠小吃(南大红门路)",
                "distance": "距市中心约15.3公里"
            },
            {
                "name": "北京毛铺大酒店",
                "pic": "http://dimg04.c-ctrip.com/images/fd/hotel/g4/M03/00/E0/CggYHVX1mquAG8lOAAC7sADB9bo760_R_550_412.jpg",
                "price": 298,
                "type": "舒适型",
                "recommend": "64%",
                "location": "丰台区呷哺呷哺",
                "distance": "距市中心约13公里"
            },
            {
                "name": "7天连锁酒店（北京丰台南路地铁站店）",
                "pic": "http://dimg04.c-ctrip.com/images/fd/hotel/g2/M03/58/50/Cghzf1WBGfOALvgHAALMPm72_Ic264_R_550_412.jpg",
                "price": 293,
                "type": "经济型",
                "recommend": "92%",
                "location": "丰台区",
                "distance": "距市中心约13.4公里"
            }
        ],
        "formatType": "list",
        "formatSpeak": "${name}，${type}，价格${price}元起，推荐度${recommend}，位于${location}，${distance}",
        "formatShow": "",
        "hintlast": "请选择"
    }
}
```




