# 1. 服务简介

波鲁鲁故事机的需求，告知故事机在某个时间点关机，故事机到点关机。产品@袁仁富。

# 2.槽位

| **Slot\_Key** | **Description** | **Example** |
| --- | --- | --- |
| date | 日期\(不带时间\) | 三天后 |
| date\_time | 时间（必需）+日期（不必需） | 明天10点、10分钟后 |

# 3.意图

\/Play

电台点播意图。用户可以根电台名称直接点播，根据电台类型进行标签点播，根据地理位置信息进行地理位置点播或者不含任何槽位的模糊点播。

| **Slot Semantic Signatures** | **Example** |
| --- | --- |
| &lt;date&gt; | 3天后关机 |
| &lt;date_time&gt; | 10分钟后关机、明天10点关机 |

返回字段

<table>

 <tr>

 <td>result</td>

 <td>value</td>

 <td>type</td>

 </tr>

 <tr>

 <td>hint</td>

 <td>好的主人，我将在xxxx自动关机</td>

 <td>string</td>

 </tr>

 <tr>

 <td>data</td>

 <td>service</td>

 <td>ShutDown</td>

 <td>string</td>

 </tr>

 <tr>

 <td></td>

 <td>Action</td>

 <td>SetShutDown</td>

 <td>string</td>

 </tr>

 <tr>

 <td></td>

 <td>alarm_time</td>

 <td>定时关机的时间，如：2017-07-31 11:04:35</td>

 <td>string</td>

 </tr>

 <tr>

 <td>formattype</td>

 <td>prop</td>

 <td>string</td>

 </tr>

 <tr>

 <td></td>

 </tr>

</table>

