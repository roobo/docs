### RML

在roobo OS中，很多规则和配置文件使用过一种特定格式的xml文件来编写。这种xml文件遵循一系列特定的标准，可以通过代码读取属性、子节点以及串入串出，我们称这种特定标准的xml为rml。

一个典型的rml片段如下面所示：

```xml
<rule id="default.pseudosleep.enter.tts">
    <condition>
        <item var1="$input:focus.tts.change.from"        opcode="equal"  var2="$null" />
        <item var1="$input:focus.tts.change.to"          opcode="not"    var2="$null" />
    </condition>
    <output>
        <item>
            <target value="ASR" />
            <action value="set_pseudosleep_mode" />
        </item>
        <item>
            <target value="SYSTEM" />
            <action value="pseudo_sleep" />
        </item>
    </output>
</rule>
```

一个rml规范的xml文档会被转换成一个RMLObject。RMLObject可以包含一系列的RMLObject作为子节点。每个RMLObject都有如下默认属性\(attribute\)：

* tag：tag名称
* name：显式声明的节点名称使用<code> name="xxx" </code>来表示。如果没有声明，则name与tag相同。
* id：使用id标识的名称。如果没有声明id，则id为空
* value：使用value标识的名称。可以通过 value="xxx" 进行显式声明。也可以使用形如<code> \<tag>xxx\</tag> </code>的方式来声明。
* children：子节点。

对应上面的片段，最顶级的节点的tag为“rule”，id为“default.pseudosleep.enter.tts”，value是空，但是包含两个child。
这些默认属性和其他的自定义属性都保存在RMLObject的attributes里面。可以通过相关接口获取属性值。

对于子节点，上面的TAG是rule的RMLObject包含两个子节点，一个是condition，一个是output。每个子节点又包含深一层次的子节点。

RMLObject能够保证节点顺序和xml文件中声明的顺序一致，但是不保证节点TAG或者ID的唯一性，多数时候只需要逐条遍历即可达到目标。如果在引用的时候指定了id，会指向第一个找到的id匹配的项。

查找节点的tag，id，value和children可以通过方便函数直接获取。

#### 引用

RML支持引用。当需要声明一个值的时候，可以通过$符号引用输入数据。引用的规则如下：

* 所有引用必须以$符号开头
* 多层次引用使用冒号“:”分割。多层次引用支持：
  * Map。通过key引用
  * List。通过下标引用
  * Bundle：通过key引用
  * Intent：通过key引用
  * RMLObject：通过属性名称或者子节点下标引用。属性名称和下标的优先级为：
    * 寻找匹配的下标（如果是数字）
    * 寻找的属性
    * 寻找匹配的tag
    * 寻找匹配的id
* 引用可以用来表示特殊的常量。目前支持的常量有：
  * $null:  表示空（null）
  * $false: 表示布尔值的False
  * $true:  表示布尔值的true
* 引用的根对象可以是：
  * input: 表示对规则的输入
  * self： 表示规则RMLObject本身。
* 如果无法找到引用的目标，返回结果是null

例如：

```xml
<ui source="weather_content"
    weather="$input:suggestion:data:0:weather"
    city="$input:suggestion:data:0:city"
    current="$input:suggestion:data:0:temperature"
    low="$input:suggestion:data:0:minTemp"
    high="$input:suggestion:data:0:maxTemp"
    receive="voice_end" execute_on_receive="stop"/>
```

weather作为ui节点的一个属性，取值为$input:suggestion:data:0:weather。这条规则的输入数据是一个bundle，其中包含一个对应key为"suggestion"的map。在这个map中有一个对应key为"data"的list。这个list的第一项是一个map，其中包含一个key为"weather"的字符串。通过引用声明，这个字符串被当作是属性weather的取值。

例如：

```xml
<rule id="online_command_wakeup">
    <condition>
        <item var1="$input:response.target" opcode="equal" var2="Wakeup" />
        <item var1="$input:response.action" opcode="equal" var2="Wakeup" />
    </condition>
    <output value="$self:voice_wakeup:output" />
</rule>
```

condition的第一个子节点中的属性var1取值为：$input:response.target。这条规则的输入数据是一个map，其中包含一个key为“response.target”的字符串。这个字符串会被赋值给var1。  
output的取值是$self:voice\_wakeup:output。在当前的规则文件中，有一个id为"voice\_wakeup"的规则。这条规则包含一个tag是"output"的子节点。这个子节点的值是一个list，会被整体赋值给当前规则的output。

### 配置文件
RML可以用于书写配置文件，几乎所有的系统服务都有对应的一个或者多个rml配置文件。一个典型的配置文件可以形如：
```xml
<?xml version="1.0" encoding="utf-8"?>
<config
    initState="sleep">
    <state
        name="active"
        falloff="5000"/>
    <state
        name="sleep"
        falloff="1800000" />
    <state
        name="deep-sleep" />
</config>
```
这个配置文件约定了电源管理模块的工作方式。这个配置文件的根节点为config，包含一个initState的属性，同时包含一系列子节点，每个子节点包含name和falloff的属性。
在代码中可以将一个xml文件串入成为一个RMLObject。读取RMLObject中的各项属性和子节点，就能得到想要的参数值了。
### 规则
RML更多的应用是用来描述规则。规则一般包含条件和输出两个部分。条件由一系列表达式组成，表达式之间以“与”或者“或”的方式一起运算，如果条件部分为真，则将输出部分描述的内容输出，否则跳过。
#### 运算符
运算符（opcode）是一个RML表达式的计算方法。例如在下面的代码片：
```xml
<item var1="$input:response.target" opcode="equal" var2="Wakeup" />
```
“equal”就是一个运算符，表示相等。如果input中的response.targe等于字符串“Wakeup”，该规则返回true，否则返回false。每条表达式都有对应的返回值。  
RML支持以下的运算符：  
  * equal：相等
  * not：不相等
  * greater：大于
  * less：小于
  * in：在列表内
  * contains：列表包含
  * minus：数字减
  * plus：数字加
  * and：逻辑与
  * or：逻辑或
  * countIn：在从现在往前的时间段内出现的次数
  * within：在从指定开始时间和结束时间的时间段内出现的次数
#### 操作符
操作数使用varX的方式表示，一般情况下，一个表达式包含两个操作数，var1和var2。特别的，within操作符需要3个操作数，var1，var2和var3。  
#### 表达式组
多个表达式之间可以通过“与”或者“或”进行运算。一个典型的表达式组的例子如下：
```xml
<rule id="online_command_wakeup">
    <condition>
        <or>
            <item var1="$input:response.target" opcode="equal" var2="Wakeup" />
            <item var1="$input:response.action" opcode="equal" var2="Wakeup" />
        </or>
        <item var1="$input:response.target" opcode="equal" var2="Chat"/>
        <not>
            <item var1="$input:scene.top" opcode="in" var2="$input:module_list"/>
        </not>
    </condition>
    <output value="$self:voice_wakeup:output" />
</rule>
```
or，not等节点包含了若干子节点，这些子节点组成了一个表达式组。表达式组输出布尔值，参与更高一级的表达式的运算。表达式组可以嵌套。  
condition节点隐含包含一个and表达式组。  
目前已经支持的表达式组有：
* and: 组内表达式进行逻辑与
* or: 组内表达式进行逻辑或，只要有一个为真，则表达式组为真
* not: 组内表达式只要有一个为假，则表达式组为假
