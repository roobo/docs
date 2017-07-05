#Action Rules

Action Rules(动作规则)描述的是系统服务(Persona)指令与Action的对应规则，使用xml格式组织。以下是规则片段：

```xml
<?xml version="1.0" encoding="utf-8"?>
<rules>
    <alias id="state">
        <constructed        value="1" type="int"/>
        <prepared           value="2" type="int"/>
        <playing_content    value="3" type="int"/>
        <running            value="4" type="int"/>
        <paused             value="5" type="int"/>
        <stopped            value="6" type="int"/>
        <ongoing            value="7" type="int"/>
    </alias>
    
    <alias id="type">
        <normal         value="0" type="int"/>
        <can_pause      value="1" type="int"/>
        <must_complete  value="2" type="int"/>
    </alias>

    <rule>
        <condition>
            <item var1="$input:action_id" type="string" opcode="equal" var2="action_1"/>
        </condition>
        <output>
            <ui action_id="action_1" action_type="can_pause" source="show_ui" />
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:action_id" opcode="equal" var2="action_2"/>
        </condition>
        <output>
            <sequential>
                <voice source="开始"/>
                <ui source="show_ui"/>
                <voice source="结束"/>
            </sequential>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:action_id" opcode="equal" var2="action_3"/>
        </condition>
        <output>
            <concurrent>
                <voice source="进行"/>
                <ui source="show_ui"/>
            </concurrent>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:action_id" opcode="equal" var2="action_4"/>
        </condition>
        <output>
            <random>
                <voice source="你好"/>
                <voice source="我能为你做些什么"/>
                <voice source="你好呀"/>
                <voice source="等待指示"/>
            </random>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:action_id" opcode="equal" var2="action_5"/>
        </condition>
        <output>
            <sequential action_id="action_5" action_type="must_complete">
                <concurrent>
                    <ui source="show_ui" />
                    <random>
                        <voice source="你好"/>
                        <voice source="我能为你做些什么"/>
                        <voice source="你好呀"/>
                        <voice source="等待指示"/>
                    </random>
                </concurrent>
                <voice source="结束"/>
            </sequential>
        </output>
    </rule>
</rules>
```

###关于$和:
节点属性值中**$**表示其后是变量名，需要引用变量获取该值。
节点属性值中**:**表示引用它前面变量中key为**:**后字符串的值。可见它必须和$一起使用才会生效，而且它要求它前面的变量必须为Map或者Bundle类型的数据。

###input变量
input变量中的值即为PersonaClient中说明的Persona指令附带的指令参数。

###根节点&lt;rules&gt;&lt;/rules&gt;

动作规则的根节点必须是&lt;rules&gt;&lt;/rules&gt;

####子节点&lt;alias&gt;&lt;/alias&gt;

```xml
<alias id="type">
    <normal         value="0" type="int"/>
    <can_pause      value="1" type="int"/>
    <must_complete  value="2" type="int"/>
</alias>
```

声明标签属性值为特定字符串时实际对应的数据类型和值。
* 标签名，即命中的字符串，比如上面的**normal**，**can_pause**，**must_complete**
* 属性type为对应的数据类型，目前支持的数量类型有：**int**, **string**, **double**, **long**, **float**和**boolean**
* 属性value为对应的值

这里声明，当标签属性值为normal，can_pause，must_complete时，它们对应的数据类型都是int型，对应的值分别为0，1，2。
这里的声明实际上只作用于Action节点的action_type属性，后面后说到。

####子节点&lt;rule&gt;&lt;/rule&gt;

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_1"/>
    </condition>
    <output>
        <ui action_id="action_1" action_type="can_pause" source="show_ui" />
    </output>
</rule>
```

条件节点用于判断指令是否满足特定条件。
每个条件标签名为item，可以有多个条件标签，他们是与的关系，其属性值有：

* **var1**: 参与比较的参数1。参数的取值可以是常量，也可以取自Persona指令附带的参数，附带的参数存在input变量中，input变量可以看做是一个Map&lt;String, Object&gt;类型的数据，可以通过分号`:`取其key为分号后字符串对应的值。
* **var2**: 参与比较的参数2。同参数1
* **type**: 所要比较的参数的类型，目前支持的类型有：**int**, **string**, **double**, **long**, **float**和**boolean**
* **opcode**: 参数比较的类型，目前支持的类型为：

|类型|要求的参数类型|
|:|:|
|**equal**|数值或者字符串|
|**not**|数值或者字符串|
|**greater**|数值|
|**less**|数值|

#####输出节点&lt;output&gt;&lt;/output&gt;

```xml
<output>
    <ui action_id="action_1" action_type="can_pause" source="show_ui" />
</output>
```

输出节点对应该动作规则输出的Action。
输出节点中的支持的Action标签名有两种类型：自定义类型和容器类型
* 自定义类型
自定义类型是由构造PersonaClient时传入的ActionFactory决定的。

```java
Map<String, IActionFactory> actionFactoryMap = new HashMap<>();
//insert ActionFactorys for face
actionFactoryMap.put("ui", new UiActionFactory());
AbsPersonaClient faceClient = PersonaClientFactory.createLocalClient(
                context,
                "face",
                "rules/action_build_rules.xml",
                "rules/action_switch_rules.xml",
                actionFactoryMap);
```

如上构造的PersonaClient说明，该PersonaClient只支持动作规则(rules/action_build_rules.xml)中的标签名为ui的Action标签。
* 容器类型

容器类型是默认支持的，目前支持的容器类型Action标签：

|type|ActionSet|
|:|:|
|**sequential**|**SequentialActionSet**|
|**concurrent**|**ConcurrentActionSet**|
|**random**|**RandomActionSet**|

**容器标签类型是支持嵌套使用的。**

###Action标签支持的属性

Action标签支持的属性有两种，固有属性和自定义属性

####固有属性

|属性|数据类型|值|说明|
|:|:|:|:|
|**action_id**|String||可选项|
|**action_type**|String|alias节点中**id**为**type**中的值|可选项，默认为**normal**|
|**delayed**|long||可选项，延迟x毫秒后执行，默认为不延时|
|**repeat**|Boolean|**true**/**false**|可选项，Action是否重复执行，即Action会循环执行，默认为false|
|**dispatch**|String||可选项，要发送的操作(operation)，必须和**dispatch_when**一起使用才会生效|
|**dispatch_when**|String|alias节点中**id**为**state**中的值|可选项，当Action处于指定状态时，发送**dispatch**属性指定的操作，必须和**dispatch**一起使用才会生效|
|**receive**|String||可选项，当接收到特定操作时，执行**execute_on_receive**指定的操作，必须和**execute_on_receive**一起使用才会生效|
|**execute_on_receive**|String|**start**，**stop**，**pause**，**resume**，**stop_immediately**|当接收到特定操作时，执行该属性指定的操作，必须和**receive**一起使用才会生效|

####自定义属性

可以自定义任意属性名，其值可以是常量，也可以从input变量中取值。比如：

```xml
<output>
    <ui action_id="action_1" action_type="can_pause" source="show_ui" />
</output>
```

这里source即为自定义的属性，这里取值为常量"show_ui"，该属性及值，会传入对应的ActionFactory中。

###示例

* 顺序执行三个Action

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_2"/>
    </condition>
    <output>
        <sequential>
            <voice source="开始"/>
            <ui source="show_ui"/>
            <voice source="结束"/>
        </sequential>
    </output>
</rule>
```

* 同时执行两个Action

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_3"/>
    </condition>
    <output>
        <concurrent>
            <voice source="进行"/>
            <ui source="show_ui"/>
        </concurrent>
    </output>
</rule>
```

* 随机执行一个Action

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_4"/>
    </condition>
    <output>
        <random>
            <voice source="你好"/>
            <voice source="我能为你做些什么"/>
            <voice source="你好呀"/>
        </random>
    </output>
</rule>
```

* 嵌套

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_5"/>
    </condition>
    <output>
        <sequential action_id="action_5" action_type="must_complete">
            <concurrent>
                <ui source="show_ui" />
                <random>
                    <voice source="你好"/>
                    <voice source="我能为你做些什么"/>
                    <voice source="你好呀"/>
                </random>
            </concurrent>
            <voice source="结束"/>
        </sequential>
    </output>
</rule>
```

* 延迟1秒执行

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_1"/>
    </condition>
    <output>
        <ui delay="1000" action_id="action_1" action_type="can_pause" source="show_ui" />
    </output>
</rule>
```

* 循环执行

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_1"/>
    </condition>
    <output>
        <ui repeat="true" action_id="action_1" action_type="can_pause" source="show_ui" />
    </output>
</rule>
```

* A Action结束后，B Action才结束

```xml
<rule>
    <condition>
        <item var1="$input:action_id" opcode="equal" var2="action_3"/>
    </condition>
    <output>
        <concurrent>
            <voice source="进行" dispatch="voice_end" dispatch_when="stopped"/>
            <ui source="show_ui" receive="voice_end" execute_on_receive="stop"/>
        </concurrent>
    </output>
</rule>
```