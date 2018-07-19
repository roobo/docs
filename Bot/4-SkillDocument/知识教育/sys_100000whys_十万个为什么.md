
# 1. 服务简介

十万个为什么

# 2.意图

### \/Play

播放用户想听的十万个为什么资源

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;category&gt; | 十万个为什么 |

_举例：数据部分_
```
    "results": [
        {
            "hint": "",
            "data": {
                "audio": "http://audio.xmcdn.com/group29/M0A/0A/20/wKgJXVlRnvTx7LroAAnlWNX_6TY276.m4a",
                "name": "为什么哭的时候会流鼻涕",
                "resId": "YWlyZXM6MTUwMDc4MA=="
            },
            "formatType": "audio"
        }
    ]
```

---


### \/Next
下一个

_举例：数据部分_
```
    "results": [
        {
            "hint": "",
            "data": {
                "audio": "http://audio.xmcdn.com/group29/M0A/0A/20/wKgJXVlRnvTx7LroAAnlWNX_6TY276.m4a",
                "name": "植物人是怎么回事",
                "resId": "YWlyZXM6MTUwMTY5Ng=="
            },
            "formatType": "audio"
        }
    ]
```

---

### \/Prev
上一个

_举例：数据部分_
```
    "results": [
        {
            "hint": "",
            "data": {
                "content": "飞机在整个飞行过程中，要利用机载无线电导航设备与地面导航台保持实时联系，以便控制飞行航线，实行安全飞行，在飞机上，使用中的手机、收音机等电子产品会发射电磁波信号，电磁波的干扰会造成飞机导航设备、自动驾驶仪系统失灵。特别是在飞机起飞、爬升和着陆阶段，由于飞机处于低空，此时的电磁波干扰更大，即使由于干扰只造成很小角度的航向偏离，也可能导致机毁人亡的后果。因此，为了保证飞机的安全飞行，在机舱内是严禁使用电子产品的。",
                "name": "机舱内为什么不能使用电子产品？",
                "resId": "YWlyZXM6MTE0NTQzMA=="
            },
            "formatType": "text"
        }
    ]
```

---

### \/Pause
暂停

---

### \/ Resume
继续播放

_举例：数据部分_
```
    "results": [
        {
            "hint": "",
            "data": {
                "content": "飞机在整个飞行过程中，要利用机载无线电导航设备与地面导航台保持实时联系，以便控制飞行航线，实行安全飞行，在飞机上，使用中的手机、收音机等电子产品会发射电磁波信号，电磁波的干扰会造成飞机导航设备、自动驾驶仪系统失灵。特别是在飞机起飞、爬升和着陆阶段，由于飞机处于低空，此时的电磁波干扰更大，即使由于干扰只造成很小角度的航向偏离，也可能导致机毁人亡的后果。因此，为了保证飞机的安全飞行，在机舱内是严禁使用电子产品的。",
                "name": "机舱内为什么不能使用电子产品？",
                "resId": "YWlyZXM6MTE0NTQzMA=="
            },
            "formatType": "text"
        }
    ]
```

---

### \/Replay
指重播当前十万个为什么（1遍）

_举例：数据部分_

```
    "results": [
        {
            "hint": "",
            "data": {
                "content": "飞机在整个飞行过程中，要利用机载无线电导航设备与地面导航台保持实时联系，以便控制飞行航线，实行安全飞行，在飞机上，使用中的手机、收音机等电子产品会发射电磁波信号，电磁波的干扰会造成飞机导航设备、自动驾驶仪系统失灵。特别是在飞机起飞、爬升和着陆阶段，由于飞机处于低空，此时的电磁波干扰更大，即使由于干扰只造成很小角度的航向偏离，也可能导致机毁人亡的后果。因此，为了保证飞机的安全飞行，在机舱内是严禁使用电子产品的。",
                "name": "机舱内为什么不能使用电子产品？",
                "resId": "YWlyZXM6MTE0NTQzMA=="
            },
            "formatType": "text"
        }
    ]
```

---

### \/Exit
退出十万个为什么场景

# 3.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| category | 十万个为什么分类 | 10万个为什么 |

# 4.返回字段描述

音频资源

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| audio | string | 播放链接 | 飞机在整个飞行过程中，要利用机载无线电导航设备与地面导... |
| name | string | 资源名 | 机舱内为什么不能使用电子产品？ |
| resId | string | 资源标识 | YWlyZXM6MTUwMDc4MA== |

文本资源

| **Field\_Name** | **Field\_Type** | **Field\_Value** | **Field\_Example** |
| --- | --- | --- | --- |
| content | string | 资源内容 | http://... |
| name | string | 资源名 | 为什么哭的时候会流鼻涕 |
| resId | string | 资源标识 | YWlyZXM6MTE0NTQzMA== |
