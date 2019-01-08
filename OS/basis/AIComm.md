### roobo OS通讯方式

com.roobo.core作为通讯系统的中心，负责接收AI事件，并向对应的[模块](module.md)发送AI命令。

#### AI事件
一个AI事件(AIEvent)是一个key，value的组合。同时，也可以指定事件的"粘性"。一个AI事件的结构如下所示：
```java
public class Event {
    public String key;
    public Serializable value;
    public boolean sticky;
}
```
粘性的事件会一直保存在Core当中，作为一个状态出现。非粘性的AI事件只会参与一次处理，无论有没有匹配到规则，都会被丢弃。

##### 发送多个AI事件
[模块](module.md)可以一次向com.roobo.core发送多个AI事件。无论是一个或者多个，每次发送AI事件会触发一次事件处理。此时所有在com.roobo.core中留存的状态与本次发送的一个或者多个AI事件结合起来，被事件处理器处理。
##### 自定义AI事件
作为模块，可以向com.roobo.core发送任何AI事件，只要遵守AI事件的规则即可：Key是一个字符串，value是一个Serializable。

对自定义的AI事件的处理可以在[pre_process.xml](processor_rules.md)和[post_process.xml](processor_rules.md)中定义。

#### AI命令
事件处理器处理事件之后，会产生一个或多个AI命令。每个命令包含四个部分：
```java
public class AICommand {
    public String target;
    public String action;
    public Bundle params;
    public Serializable suggestion;
}
```
其中params和suggestion的具体数据类型需要参考AI相关场景定义或者自己指定。
对于场景，params和action一起定义了用户意图。如果roobo同时提供了对应的云服务，那么可以在suggestion中找到该云服务返回的数据。
对于其他类型的模块，例如服务或者普通模块，suggestion中可能不包含任何数据。
