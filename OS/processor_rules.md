### 事件处理器规则

事件处理器的规则写在preprocess.xml和post\_process.xml里面。分别对应前处理器和后处理器_。  
_事件处理器规则的根节点是rules。  
每条规则的tag都是rule。规则包括两个子节点：condition和output。

#### rule

rule节点标识一条规则。可选的属性有：

* id：标识这个节点的id。  
* absorb：只针对前处理器有效。表示这个规则执行完成后是否要送入云端处理器进行处理。默认是ture。表示如果匹配到了前处理器的某条规则，就不会再送到云端。

#### condition

condition节点标识一条规则的匹配项。condition下可以有很多子节点，每个节点的tag都是item。如果所有这些匹配子节点都匹配成功，就认为这一条规则匹配成功。

一个子节点对应一个判断表达式，包括如下几个属性：

* var1:比较数。一个比较数可以是任何Serializable类型。
* opcode:比较操作符。可以取值为：
  * equal
  * not
  * greater
  * less 
* var2:被比较数。一个被比较数可以使任何Serializable类型。
* type:如果被比较数是通过字符串描述而不是引用描述，例如：“1”，需要type来标明被比较数的类型。如果不指定type，默认是字符串类型。

#### output

output节点表示一条规则的输出项。对于每一条规则，输入项是若干K-V对，输出项则是一个AICommand的列表。每个output子节点都表示一个AICommand。例子如下：

```
<target value="SYSTEM" />
<action value="asr.status" />
<params>
    <status type="int" value="$input:asr.status" />
</params>
```

这个command的target是SYSTEM，action是asr.status，params里面只包含一个KV对，key是"status"，value是当前asr的状态，从输入的aievent当中取出。

如果某个规则的output和另外一条规则的output完全相同，可以使用类似下面的引用：

```
<rule id="online_command_wakeup">
    <condition>
        <item var1="$input:response.target" opcode="equal" var2="Wakeup" />
        <item var1="$input:response.action" opcode="equal" var2="Wakeup" />
    </condition>
    <output value="$self:voice_wakeup:output" />
</rule>
```

这条规则的output引用了当前xml文件中的一个id是voice\_wakeup的output项。

也可以用下面的方法引用输入的params:

```
<item>
    <target value="PERSONA" />
    <action value="$input:response.action" />
    <suggestion value="$input:response.suggestion" />
    <params value="$input:response.params" />
</item>
```



