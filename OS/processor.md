### 事件处理器

事件处理器是语义处理过程的一部分。包括前处理器（Pre Processor）和后处理器（Post Processor）。语音识别结果通过首先发送到前处理器，如果前处理器没有吸收，则发送到云端进行语义分析。此后发送到后处理器再次处理。随后转化为AI指令发送到各个场景和模块。请参考[用户交互过程](full_interaction_process.md)

#### 前处理器
语音识别结果首先会进入到前处理器。因为不需要经过语义云，所以前处理器获取数据几乎不消耗时间。非常适合做一些本地事件的处理。例如触摸机器人的身体或者四肢，电源适配器被拔出之后的相应等等。也可以做一些简单的本地逻辑。前处理器对AI事件的处理是通过规则来确定的。典型的前处理器规则片段代码如下：
```xml
<rule id="mainmenu">
    <condition>
        <item var1="$input:asr.text" opcode="equal" var2="所有功能"/>
    </condition>
    <output>
        <item>
            <target value="MAINMENU"/>
            <action value="Show"/>
        </item>
    </output>
</rule>
```

这段规则表示如果遇到识别结果是“所有功能”四个字，就启动MainMenu。这样就相当于简单的语义处理。

如果规则的output节点是空，就表示什么都不输出。效果类似把事件屏蔽掉了。例子如下：
```xml
<!-- filter the junk from asr -->
<rule id="default.voice.filter_junk.1">
    <condition>
        <item var1="$input:asr.text" opcode="equal" var2="。" />
    </condition>
    <output/>
</rule>
```

如果需要在前处理器匹配成功之后不吸收事件，仍然发送到语义云，需要在rule节点加上absorb="false"。

#### 后处理器
语音识别结果经过语义云转化为语义，随后进入后处理器。后处理器可以实现场景转发或者场景拒识等功能。场景转发的代码片段如下：
```xml
<rule id="redirect_chat">
    <condition>
        <item var1="$input:response.target" opcode="equal" var2="Chat" />
    </condition>
    <output>
        <item>
            <target value="PERSONA" />
            <action value="Chat" />
            <suggestion value="$input:response.suggestion" />
            <params value="$input:response.params" />
        </item>
    </output>
</rule>
```
上面的代码表示，如果有场景名称为Chat的语义指令，就将其转发给Persona。

场景拒识的典型代码片段如下：
```xml
<rule id="filter_profile">
    <condition>
        <item var1="$input:response.target" opcode="equal" var2="Profile" />
        <item var1="$input:scene.top" opcode="not" var2="$null" />
    </condition>
    <output/>
</rule>
```
上面的代码表示，仅仅在没有场景的时候才响应画像的对话请求。