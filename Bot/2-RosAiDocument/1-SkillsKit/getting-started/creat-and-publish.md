# 创建你的第一个BOT

本文档从BOT创建，BOT开发，BOT测试，BOT发布，BOT版本管理等方面讲解如何在ROS.AI平台上实现BOT。 

## BOT创建

登录ROS.AI平台，进入Bot服务，选择“Bot管理”，点击“新建BOT”，输入”BOT名称”，“BOT描述”完成BOT创建。
![image](images/build-bot.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/build-bot1.png)




## BOT开发

BOT创建成功后，点击BOT，进入BOT管理界面，如下图所示
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/bot-basic-info.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/bot-basic-info_server-address.png)




### 1. 基本信息

（1）   可对“BOT名称”，“BOT描述”进行修改

（2）   可上传该BOT专属LOGO

（3）   可勾选第三方服务，输入服务地址用于增强BOT能力

（4）   可自主选择机器人学习能力：精确，智能

### 2. 交互模型

#### 2.1 意图

意图是指用户说话的目的，当用户说“我想查询天气”时，查询天气就是用户的意图。

定义一个意图包括意图基本信息，模板，参数

（1）   基本信息
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/intent-base-info.png)


（2）   模板

意图创建成功后，可以添加该意图下的模板。模板即用户query时需满足的句式，用户query满足该模板，该意图才会进行响应。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/Template.png)


（3）   参数

   意图，模板创建成功后，可以对模板中含有的参数指定实体和值。

   实体的指定：可引用系统实体，也可引用自己创建的实体。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/parameter.png)


#### 2.2 子模板

表示能抽象出来的一类小模板，用于丰富模板。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/Subtemplate.png)


在模板中的引用如下图
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/subtemplate-in-template.png)


#### 2.3 实体

实体是用户与BOT交互过程中的一个重要概念，是指某领域词汇的集合。当用户询问北京天气怎么样时，其中北京是城市信息，将北京，上海等所有城市信息集合起来就组成了中国城市的实体。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/entity_basic%20info.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/entity-item_synonym.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/entity-item.png)
 







## BOT测试

当BOT创建，开发完后，需要对BOT进行测试，确认BOT是否满足设计的交互场景。

在测试前需点击“编译”，会生成一个进行中的模型，在下方测试窗口可进行测试。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/bot-compile.png)


（1）基本信息中没有输入第三方服务地址，且不带参数的查询。会返回匹配到的BOT service和意图action，如下图
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/intent-test.png)


（2）基本信息中没有输入第三方服务地址，且带参数的查询。会返回匹配到的BOT service和意图action，如下图
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/intent-para-test.png)


（3）基本信息中输入第三方服务地址。会返回查询的结果。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/intent-addr-test.png)


## BOT发布

当BOT经过测试后，可以将BOT发布到AI助手管理中。

在模拟测试中，在当前进行中的模型中点“发布”，填写版本号及版本描述信息之后，可将BOT的该版本发布到AI助手管理中。

![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/Release.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/version-info.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/ai-assistant.png)





## BOT版本管理

发布成功的版本会出现在版本管理中。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/version-manage.png)


可对BOT进行修改，进行多次版本发布，也可对版本进行回滚，但目前只支持一个版本发布到AI助手管理中。
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/online-version.png)
![image](https://github.com/roobo/docs/blob/master/Bot/2-RosAiDocument/1-SkillsKit/getting-started/images/RollBACK.png)




 

 

 

 

 

 

