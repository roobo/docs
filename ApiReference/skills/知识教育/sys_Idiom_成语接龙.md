# 1. 服务简介

为用户提供成语接龙服务服务。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| idiom | 成语 | 厚德载物 |
| any | 用户的输入\(不是成语\) |  |

# 3.意图

\*\*\*Play意图和Repeat意图的返回字段相同，在此统一说明

| **result** |  | **value** | **type** |
| --- | --- | --- | --- |
| hint |  | 机器人说的成语 | string |
| data | idiomToMatch | 机器人说的成语 | string |

\/Play

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
|  | 成语接龙 |
| &lt;idiom&gt; | 厚德载物 |

\/Repeat

\/GiveTips

\/GiveAnswer

\/Replay

\/Pause

\/Save

\/Exit

