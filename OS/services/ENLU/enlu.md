### 离线NLU
NLU（Natual Language Understanding，自然语言理解）是语音交互系统中非常重要的处理单元。NLU接收用户的query（文本形式），通过对语义进行分析，抽取出槽位，返回用户意图。

roobo提供AI平台供开发者使用。除此之外，也提供基于模板匹配的离线NLU，帮助开发者快速实现定制化需求。
#### 上下文
一个场景可以看作是一个有向图，图中的每个节点表示一个状态，每条边表示从一个状态切换到另外一个状态的路径，对于语音操作，这条边是用户意图(intent)。

一个用户意图可以从一个状态切换到另外一个状态。用户意图起点对应的状态称作这个意图的上文，用户意图终点对应的状态称作这个意图的下文。一个状态既可以作为某个意图的上文，同时也可以作为另外一个意图的下文。

不但语音操作可以引起上下文的切换，GUI操作也可以产生同样的效果。一个应用程序如果希望GUI和VUI协同工作，需要有意识地设置上下文。
设置上下文的方式请参考：[场景服务](../sceneservice.md)
#### 模板
一个简单的理解用户语义的方式是预置一系列的句式，形如：
```xml
<intent input_context="*">
    <action value="open_road_condition" />
    <templates>
        <item>[帮我|我要|][打开|开启|查看]路况</item>
    </templates>
</intent>
```
这个模板指定了一系列用户的可能query。包括：帮我打开路况，开启路况等。
如果用户query与这条模板匹配，就返回意图：open_road_condition。
#### 槽位
上面介绍的模板只是覆盖特定的句式，很多时候，我们希望将句子中的某些文字抽取出来，转化为槽位返回。例如：
```xml
<intent input_context="Child_Home">
    <action value="Switch_Bottom_Tab" />
    <templates>
        <item>[切换|切换到|切到][$bottom_tab_name:tabname][页面|界面|页|]</item>
    </templates>
    <params>
        <tabname>$tabname</tabname>
    </params>
</intent>
```
在上面的句式中，我们引入了实体 bottom_tab_name，表示页面标签名称。该实体的规约词可能是这个标签的序号或者id。如果用户query与该条模板匹配，对应的标签的id就会被作为参数返回，参数名是：tabname。

通过这种方式，制定一系列模板和槽位，可以让用户应用程序具备一定的语音交互能力。
#### 离线NLU与在线NLU的关系与选择
按照语义理解的方式，可以将引擎分为基于规则与基于统计两种。 

基于规则的语义理解预先设定规则，将用户的query与规则进行比较，如果符合预定义的模式，就可以获得对应的语义和槽位。这种方式的优势是匹配精准，实施快速，无需训练语料，通过配置模板就可以完成语义理解的功能。缺点是几乎没有泛化能力，需要预先猜测用户可能的说法，如果猜测出错，即便是有很小的出入，也无法完成功能。  

基于统计的语义理解则是将用户query通过预处理，转换成向量或者向量序列，随后通过一个预先训练好的模型对这个向量或向量序列进行分类和标注，获取意图及槽位。这种方法的优势是泛化能力非常强，通过一段时间的训练，可以非常宽泛的覆盖用户的说法。缺点是根据业务的不同，需要大量的训练语料，同时因为统计本身的局限性，总会存在badcase。  

合理的将两种方式的语义理解结合起来，可以实现比较好的工程效果。一般来说，离线NLU执行快速，配置简单，非常适合用于GUI操作以及一些简单的列表选择。例如，可以通过配置离线NLU实现对页面的切换和分类标签选择，对多条导航搜索结果进行前后翻页，指定选择某一条等。  

对于一些可以抽象为模板但是需要在云端动态调整的场景，需要在云端使用基于规则的方式进行处理。对于一些需要很强泛化能力的场景，以及一些对数据有要求的场景，只能使用在线NLU。例如点播音乐，新闻查询，知识库问答等。
