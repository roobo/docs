# 1.服务背景

增加，查询，删除，延迟闹钟的语义服务。

# 2.槽位

| Slot key | Description | Application | Example |
| --- | --- | --- | --- |
| specific\_time | 具体时刻 | 用户设置，删除闹钟等 | 9点20分 |
| specific\_date | 具体日期 | 用户设置，删除闹钟等 | 2月20日 |
| periodic\_time | 周期时刻 | 用户设置，删除闹钟等 | 每天10点 |
| periodic\_date | 周期日期 | 用户设置，删除闹钟等 | 每周五下午 |
| event\_name | 事件名称 | 用户设置提醒时 | 做作业 |

# 3.意图

## 3.1 SetClock\_设置闹钟



