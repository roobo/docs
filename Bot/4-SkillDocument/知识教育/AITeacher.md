# 1.技能简介

AITeacher 安装在ai老师项目个人账号下，提供语义解析和英文释义功能，帮助客户端更好的实现ai教育各个场景。

# 2.技能安装指导

一个技能无法保证适用于所有产品，这里会列举出一些我们的场景接入建议，帮助用户做出决策。
该场景仅安装在ai老师项目个人账号下，不提供场景商店安装。

# 3.返回槽位说明

技能平台分析过后会产生槽位信息，此处是该技能返回的槽位的集合，槽位名一致时槽位意义相同，不区分意图。

| **Slot** | **Description** | **Example** |**Value** | **Type** |
| ------------ | ------------ | ------------ | ------------ | ------- |
| course_words | 课程词汇 | pizza是什么意思 | pizza | String |
| module | 学习的模块名 | 我要学习字母跟读 | 字母跟读 | String |
| topic | 学习的主题名 | 我要学习topic one字母跟读 | topic one | String |
| page_number | 翻页的页码 | a.我要看第10页<br/>b.trun to page ten | a.10<br/>b.ten | String |

# 4.返回意图说明

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

<td>Start</td>

  <td >Start</td>

   <td >开始进入学习模块</td>

   <td>a.我要学习绘本</br>b.我要学习游戏</td>
   
   <td>无</td>
   
 <td rowspan="9">上文：ai_teacher</br>下文：ai_teacher</td>

</tr>

<tr>

<td rowspan="2">ChangeModule</td>

  <td >ChangeModule</td>

   <td >选择学习模块</td>

   <td>a.我要学习字母跟读</br>b.我想玩字母游戏</td>
   
   <td>module</td>

</tr>

<tr>

  <td >ChangeModuleByTopic</td>

   <td >通过主题精准的选择学习模块</td>

   <td>a.我要玩topic one字母游戏<</td>
   
   <td>topic</td>

</tr>

<tr>

  <td >Pause</td>

  <td >Pause</td>

   <td >暂停</td>

   <td>a.可以休息一会儿吗<br/>b.暂停</td>
   
   <td>无</td>

</tr>

<tr>

  <td >Resume</td>

  <td >Resume</td>

   <td >继续</td>

   <td>a.继续学习<br/>b.go on</td>
   
   <td>无</td>

</tr>

<tr>

  <td >PrevPage</td>

  <td >PrevPage</td>

   <td >上一页</td>

   <td>a.我要看上一页<br/>b.pageup</td>
   
   <td>无</td>

</tr>

<tr>

  <td >NextPage</td>

  <td >NextPage</td>

   <td >下一页</td>

   <td>a.我要看下一页<br/>b.pagedown</td>
   
   <td>无</td>

</tr>

<tr>

  <td >TurnPage</td>

  <td >TurnPage</td>

   <td >精准翻页</td>

   <td>a.我要看第一页<br/>b.turn to page one</td>
   
   <td>无</td>

</tr>



<tr>

  <td >EnglishExplanation</td>

  <td >EnglishExplanation</td>

   <td >英文释义</td>

   <td>a.pizza是什么意思<br/>b.what is plane</td>
   
   <td>无</td>

</tr>

<tr>

  <td >Exit</td>

  <td >Exit</td>

   <td >退出</td>

   <td>a.退出<br/>b.quit</td>
  <td >无</td>
   <td>上文：ai_teacher</br>下文：无</td>

</tr>

</table>

### 事件触发意图
<table>

<tr>

<td><b>Intent</b></td>

<td><b>SubIntent</b></td>

<td><b>Description</b></td>

<td><b>Logic</b></td>

</tr>

<tr>

  <td >Distracted</td>

  <td >Distracted</td>
 <td ></td>
  <td ></td>

</tr>

<tr>

  <td >Concentrated</td>

  <td >Concentrated</td>
 <td >集中，由事件触发</td>
  <td >集中，由事件触发</td>

</tr>


</table>

# 5.返回字段说明
场景返回字段不区分意图，不同意图下，相同字段意义一致

| **result** | **Description** | **value** | **type** |**Required** |
| ------------ | ------------ | ------------ | ------------ |------------ |
| image | 资源的图片信息 | http://xxx/xxx.png | string |Required|
| desc | 资源的描述信息 | this is train.train is a transport. | string |Optional|
| audio | 资源的视频信息 | http://xxxx/xx.mp3 | string |Optional|

# 6.语义测试
运行语义测试前请确保：

1.拥有ros.ai 开发平台账号

2.确认该账号下要测试的场景已经打开

[语意测试连接](https://passport.ros.ai/#/login)




