#Action Switch Rules

Action Switch Rules描述的是PersonaClient中Action的状态切换规则和Action的切换规则。 

以下是标准的切换规则，一般来说，使用该规则即可满足需求。如果有其它的需求，在合适的位置加上特定的规则即可。

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
        <pausible       value="1" type="int"/>
        <must_complete  value="2" type="int"/>
    </alias>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="constructed"/>
        </condition>
        <output>
            <current value="prepare"/>
            <queued value="$null"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="prepared"/>
        </condition>
        <output>
            <current value="start"/>
            <queued value="$null"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="equal" var2="$null"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="prepare"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="equal" var2="$null"/>
            <item var1="$input:queued" opcode="equal" var2="$null"/>
            <item var1="$input:pending" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="$null"/>
            <pending value="resume"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="stopped"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="prepare"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="paused"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="prepare"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="stopped"/>
            <item var1="$input:queued" opcode="equal" var2="$null"/>
            <item var1="$input:pending" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="$null"/>
            <pending value="resume"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="paused"/>
            <item var1="$input:queued" opcode="equal" var2="$null"/>
            <item var1="$input:pending" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="$null"/>
            <pending value="resume"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="running"/>
            <item var1="$input:current:type" opcode="equal" var2="normal"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="stop"/>
            <queued  value="$null"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="running"/>
            <item var1="$input:current:type" opcode="equal" var2="pausible"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="pause"/>
            <queued  value="$null"/>
            <pending value="$null"/>
        </output>
    </rule>

    <rule>
        <condition>
            <item var1="$input:current" opcode="not" var2="$null"/>
            <item var1="$input:current:state" opcode="equal" var2="running"/>
            <item var1="$input:current:action_type" opcode="equal" var2="must_complete"/>
            <item var1="$input:queued" opcode="not" var2="$null"/>
        </condition>
        <output>
            <current value="$null"/>
            <queued  value="$null"/>
            <pending value="$null"/>
        </output>
    </rule>
</rules>
```

Action切换规则和Action规则的语法是一致的，这里将不再解释。

###关于input变量
input变量中包含了3个Action，分别为：
* 当前Action: **$input:current**
* 队列中的第一个Action: **$input:queued**
* Action栈(被暂停的Action)中栈顶Action: **$input:pending**

Action变量支持的参数(下面仅以**$input:current**为例，其它也是一样的)：
* **$input:current:id**: 只有在Action规则的输出的根Action标签指定了action_id属性的的Action，才有这个参数
* **$input:current:type**: Action的类型，取值为alias中id为type中的值
* **$input:current:state**:  Action当前的状态，取值为alias中id为state中的值

###条件节点

```xml
<condition>
    <item var1="$input:current" opcode="not" var2="$null"/>
    <item var1="$input:current:state" opcode="equal" var2="running"/>
    <item var1="$input:current:action_type" opcode="equal" var2="must_complete"/>
    <item var1="$input:queued" opcode="not" var2="$null"/>
</condition>
```

条件节点中的每一个条件其实是通过对input变量中三个Action及其参数的比较来完成的。

###输出节点

```xml
<output>
    <current value="prepare"/>
    <queued value="$null"/>
    <pending value="$null"/>
</output>
```

输出节点输出的是每个Action接下来要执行的操作(operation)。如上是指，当前Action需要执行prepare操作，队列中的和栈中的没有操作要执行。

###规则解析
* 规则1：当前Action构造完后进行准备
	* 条件
		* 当前Action不为空
		* 当前Action的状态为constructed
	* 输出
		* 当前Action执行prepare操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="constructed"/>
    </condition>
    <output>
        <current value="prepare"/>
        <queued value="$null"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则2：当前Action准备完后开始执行
	* 条件
		* 当前Action不为空
		* 当前Action的状态为prepared
	* 输出
		* 当前Action执行start操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="prepared"/>
    </condition>
    <output>
        <current value="start"/>
        <queued value="$null"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则3：当前没有Action，执行队列中的Action
	* 条件
		* 当前Action为空
		* 队列中有Action
	* 输出
		* 切换当前Action为队列中的队首Action，并执行prepare操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="equal" var2="$null"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="prepare"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则4：当前没有Action，也没有排队的Action，则恢复被暂停的Action
	* 条件
		* 当前Action为空
		* 队列中没有Action
		* Action栈中有暂停的Action
	* 输出
		* 切换当前Action为Action栈栈顶的Action，并执行resume操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="equal" var2="$null"/>
        <item var1="$input:queued" opcode="equal" var2="$null"/>
        <item var1="$input:pending" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="$null"/>
        <pending value="resume"/>
    </output>
</rule>
```

* 规则5：当前Action执行到stopped状态，即执行结束，执行队列中的Action
	* 条件
		* 当前Action不为空
		* 当前Action的状态为stopped
		* 队列中有Action
	* 输出
		* 切换当前Action为队列中的队首Action，并执行prepare操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="stopped"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="prepare"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则6：当前Action已经出去paused状态，队里中来了Action，执行队列中Action
	* 条件
		* 当前Action不为空
		* 当前Action的状态为paused
		* 队列中有Action
	* 输出
		* 将当前Action推入Action栈中
		* 切换当前Action为队列中的队首Action，并执行prepare操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="paused"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="prepare"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则7：当前Action执行完毕，又没有排队的Action，则恢复被暂停的Action
	* 条件
		* 当前Action不为空
		* 当前Action的状态为stopped
		* 队列中没有Action
		* Action栈中有Action
	* 输出
		* 切换当前Action为Action栈中的栈顶Action，并执行resume操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="stopped"/>
        <item var1="$input:queued" opcode="equal" var2="$null"/>
        <item var1="$input:pending" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="$null"/>
        <pending value="resume"/>
    </output>
</rule>
```
i
* 规则8：当前Action进入paused状态，又没有排队的Action，则恢复栈顶的Action，并将当前Action压入栈中
	* 条件
		* 当前Action不为空
		* 当前Action的状态为paused
		* 队列中没有Action
		* Action栈中有Action
	* 输出
		* 切换当前Action为Action栈中栈定的Action，并执行resume操作
		* 将当前Action压入Action栈中

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="paused"/>
        <item var1="$input:queued" opcode="equal" var2="$null"/>
        <item var1="$input:pending" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="$null"/>
        <pending value="resume"/>
    </output>
</rule>
```

* 规则9：当前Action处于running状态，当前Action类型如果是normal的，将会被新来的Action打断，即终止执行
	* 条件
		* 当前Action不为空
		* 当前Action的状态为running
		* 当前Action的类型为normal
		* 队列中有Action
	* 输出
		* 当前Action执行stop操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="running"/>
        <item var1="$input:current:type" opcode="equal" var2="normal"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="stop"/>
        <queued  value="$null"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则10：当前Action处于running状态，当前Action如果是可暂停的，则执行pause操作
	* 条件
		* 当前Action不为空
		* 当前Action的状态为running
		* 当前Action的类型为pausible
		* 队列中有Action
	* 输出
		* 当前Action执行pause操作

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="running"/>
        <item var1="$input:current:type" opcode="equal" var2="pausible"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="pause"/>
        <queued  value="$null"/>
        <pending value="$null"/>
    </output>
</rule>
```

* 规则11：当前Action处于running状态，当前Action的类型如果是must_complete，那么新来的Action没法打断当前
	* 条件
		* 当前Action不为空
		* 当前Action的状态为running
		* 当前Action的类型为must_complete
		* 队列中有Action
	* 输出
		* 空

```xml
<rule>
    <condition>
        <item var1="$input:current" opcode="not" var2="$null"/>
        <item var1="$input:current:state" opcode="equal" var2="running"/>
        <item var1="$input:current:action_type" opcode="equal" var2="must_complete"/>
        <item var1="$input:queued" opcode="not" var2="$null"/>
    </condition>
    <output>
        <current value="$null"/>
        <queued  value="$null"/>
        <pending value="$null"/>
    </output>
</rule>
```

