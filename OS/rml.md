### RML

在roobo OS中，很多逻辑是通过规则文件来表达的。通过规则文件，开发者可以快速的修改原有或者产生新的规则。  
规则文件使用xml方式书写。遵循一系列特定的标准。我们称这种特定的标准化的xml为rml。

一个最简单的rml片段如下面所示：

```
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

* TAG：tag名称
* ID：使用id标识的名称
* VALUE：使用value标识的名称。

这些默认属性和其他的自定义属性都保存在RMLObject的attributes里面。可以通过相关接口获取属性值。

对于子节点，上面的TAG是rule的RMLObject包含两个子节点，一个是condition，一个是output。每个子节点又包含深一层次的子节点。

RMLObject能够保证节点顺序和xml文件中声明的顺序一致，但是不保证节点TAG或者ID的唯一性，多数时候只需要逐条遍历即可达到目标。如果在引用的时候指定了id，会指向第一个找到的id匹配的项。

查找节点的TAG，ID和VALUE可以通过方便函数直接获取。

#### 引用

RML支持引用。当需要声明一个值的时候，可以通过$符号引用输入数据。引用的规则如下：

* 所有引用必须以$符号开头
* 多层次引用使用冒号“:”分割。多层次引用支持：
  * Map。通过key引用
  * List。通过下标引用
  * Bundle：通过key引用
  * Intent：通过key引用
  * RMLObject：通过属性名称或者子节点下标引用。属性名称和下标的优先级为：
    * 下标
    * 名为Name的属性
    * TAG
    * ID
* 引用可以用来表示特殊的常量。目前支持的常量有：
  * $null:  表示空（null）
  * $false: 表示布尔值的False
  * $true:  表示布尔值的true
* 引用的根对象可以是：
  * input: 表示对规则的输入
  * self： 表示规则RMLObject本身。
* 如果无法找到引用的目标，返回结果是null

例如：

```
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

```
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

