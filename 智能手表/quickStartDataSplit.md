### 场景是数据什么
每一个场景想完成对应的功能,比如需要对应的数据.这些数据跟ROS.AI 和 本地转发规则都是密不可分的.ROS.AI返回的数据,经过本地整理转发后场景收到数据,就是场景数据.

### 规则系统
规则系统有专门章节去详细介绍. 本章只使用不做详解.
系统有前处理器 和 后处理器. 可以简单的认为一些本地AI能处理的问题都在前处理器中. 需要经过ROS.AI的指令会在后处理中得到处理. 一个事情总是先经过 前处理器,然后再到后处理器. 来找寻匹配这个事情的规则.找到匹配规则后不在往下. 规则总是从规则文件上方开始.依次遍历匹配.

### 拆分数据
前处理器对应规则文件 : **pre_process.xml**
后处理器对应规则文件 : **post_process.xml** 


示例工程中
**resource/sdcard/ros/configure/**  的两个文件一个分别对应前后处理器.将文件push到设备的**/sdcard/ros/configure/** 目录下. 就可以将该规则添加到对应处理器规则的顶部. 这样我们修改的规则就有优先匹配权. 如 :RooboShowMsg 这个app 的场景是"SHOW_MSG". 系统唤醒的指令发到了这个场景,所以

#### **pre_process.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<rules>
    <!--语音唤醒 start -->
    <rule id="new_voice_wakeup">
        <condition>
            <item opcode="equal" var1="$input:asr.command" var2="wakeup" />
        </condition>
        <output>
            <item>
                <target value="Core.CloudAI" />
                <action value="reset" />
            </item>
            <item>
                <target value="Core.EventHub" />
                <action value="reset" />
            </item>
            <item>
                <target value="Core.PowerManager" />
                <action value="userActivity" />
            </item>
            <item>
                <target value="Core.SceneManager" />
                <action value="reset" />
            </item>
            <item>
                <target value="Core.PermissionManager" />
                <action value="reset" />
            </item>
            <item>
                <target value="SHOW_MSG" />
                <action value="wakeup" />
            </item>
        </output>
    </rule>
    <!--语音唤醒 end -->
</rules>
```

新增内容
```xml
<item>
    <target value="SHOW_MSG" />
    <action value="wakeup" />
</item>
```

因为规则匹配后将不会继续,所以我覆盖原有的唤醒规则后, 为了保证系统正常运行也需要把原先规则所做的事情做一遍. 目前还未添加规则继承. 若开发者有其余场景需要接收该消息可以在此修改. 想要了解更多的系统指令请通过商务联系我们.

#### **post_process.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<rules>
    <rule id="SHOW_MSG_all_pass">
        <condition>
            <item opcode="not" var1="$input:response.target" var2="$null" />
            <item opcode="not" var1="$input:response.action" var2="$null" />
        </condition>
        <output>
            <item>
                <target value="SHOW_MSG" />
                <action value="$input:response.action" />
                <params value="$input:response.params" />
                <suggestion value="$input:response.suggestion" />
            </item>
        </output>
    </rule>

    <!-- 自动休眠 start -->

    <rule id="sleep">
        <condition>
            <item opcode="equal" var1="$input:response.action" var2="SetSleep" />
            <item opcode="equal" var1="$input:response.target" var2="Sleep" />
        </condition>
        <output>
            <item>
                <target value="Core.EventHub" />
                <action value="reset" />
            </item>
            <item>
                <target value="Core.PowerManager" />
                <action value="sleep" />
            </item>
            <item>
                <target value="Core.SceneManager" />
                <action value="reset" />
            </item>
            <item>
                <target value="PERSONA" />
                <action value="SetSleep" />
            </item>
            <item>
                <target value="ASR" />
                <action value="sleep" />
            </item>
            <item>
                <target value="SYSTEM" />
                <action value="sleep" />
            </item>
            <item>
                <target value="SHOW_MSG" />
                <action value="sleep" />
            </item>
        </output>
    </rule>
    <!-- 自动休眠 end -->
</rules>

```

**SHOW_MSG_all_pass**   id 的名字可以修改,英文加下划线即可, 尽可能不要重复.
该条规则已经写名  当响应的response.target 和 response.action 均不为 null 的时候将数据转发给 <output> 标签中制定的target ,也就是 SHOW_MSG.
想让我们建立的Pudding 场景应该怎么做呢.
这是我们建立的ROS.AI场景. 写明service 是 Pudding , 所以到规则中 response.target 的值也会时 Pudding
![](/OS/assets/quick_start_7.png)   


而下图中的 意图名称   ask , eat ,praise  这三个是 response.action
 ![](/OS/assets/quick_start_8.png)
 
为此在**post_process.xml** 顶端加了一条新的规则

```xml
<rule id="Pudding_all_pass">
        <condition>
            <item opcode="equal" var1="$input:response.target" var2="Pudding" />
        </condition>
        <output>
            <item>
                <target value="$input:response.target" />
                <action value="$input:response.action" />
                <params value="$input:response.params" />
                <suggestion value="$input:response.suggestion" />
            </item>
        </output>
    </rule>
```
 
 然后将修改后的 **post_process.xml**文件重新push到 **/sdcard/ros/configure/** 目录下.
 按顺序重启进程:
 
 1.com.roobo.platformservice:configure
 2.com.roobo.platformservice:core
 3.com.roobo.platformservice:asr
 
 

根据我们在ROS.AI 配置的意图: ask , eat ,praise

打开RooboDemo 按住按键说出: **布丁你在哪里** 处触发 ask 意图 从而进入 Pudding 场景. 
![](/OS/assets/quickStartDataSplit_1.png)
说出: **我要吃布丁**  和 **布丁真好吃** . 都会有对应的 tts 变化.
至此 拆分场景数据已经完成.  更好的写好规则可以查阅  **规则系统**章节 .

