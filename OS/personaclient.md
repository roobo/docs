# PersonaClient

PersonaClient是一个AI指令执行端。它将自己注册到相关的系统服务\(以下会简称该服务为Persona\)中，以接收Persona的指令并执行。

### Persona指令形式

Persona下发的指令的所有参数都会被放到一个Bundle类型的对象中，包含以下数据：

|key|type|
|:|:|
|**action_id**|String|
|**params**|Bundle|
|**suggestion**|Serializable|

### 指令的解释及执行

* PersonaClient会将所有要执行的指令解释成相应的动作（Action，解释的规则请参照动作规则），并将之加入到Action队列中，然后根据动作切换规则改变当前动作的执行状态。

### Action队列和Action栈

PersonaClient维护着一个Action队列和一个Action栈：

* Action队列
  PersonaClient会将要执行的Action加入Action队列，也就是说Action的执行是串行的。
  但要注意的是，队列中每有新的Action加入，除新加入的Action外，Action类型为normal的Action都会被清除。
* Action栈
  Action类型为can\_pause的Action，当被打断时\(即有新的Action加入Action队列中\)，会被压入Action栈。

### PersonaClient API

* PersonaClient

```java
/**
 * @return 返回PersonaClient类型
 */
public String getType();
/**
  * @param listener 设置PersonaClient状态监听
  */
public void setClientListener(PersonaClientListener listener);
/**
 * 将PersonaClient注册到系统服务(Persona)
 */
public void connect();
/**
 * 将PersonaClient从系统服务(Persona)中注销
 */
public void disconnect();
/**
 * 向PersonaClient提交Action请求
 * 
 * @param sequenceId 当前请求的Action的标识id，格式无要求，唯一即可
 * @param action 所请求的Action的参数信息
 * @param packageName 请求方包名，未使用
 */
public void requestAction(String sequenceId, Bundle action, String packageName);
```

* PersonaClientListener

```java
/**
 * 通知PersonaClient已准备好
 * 
 * @param type PersonaClient类型
 */
void onClientReady(String type);

/**
 * 通知有新的Action请求
 * 
 * @param actionId 请求的actionId
 */
void onActionRequest(String actionId);

/**
 * 通知有新的Action开始执行
 * 
 * @param sequenceId 执行Action的标识id
 */
void onActionStart(String sequenceId);

/**
 * 通知当前Action执行结束
 * 
 * @param sequenceId 执行Action的标识id
 */
void onActionFinished(String sequenceId);
```

### 创建PersonaClient

PersonaClientFactory是用于创建PersonaClient的工厂类，提供两个接口：

```java
/**
  * @param c Context
  * @param type PersonaClient类型，用于在系统服务(Persona)中唯一标识
  * @param actionRulesFile 动作规则xml文件路径(相对于assets)
  * @param switchRulesFile 动作切换规则的xml文件路径(相对于assets)
  * @param actionFactoryMap 所有用于解释actionRulesFile的Action工厂类
  * @param listener PersonaClient状态监听器
  * @return PersonaClient
  */

public static AbsPersonaClient createLocalClient(Context c, String type, String actionRulesFile, String switchRulesFile, Map<String, IActionFactory> actionFactoryMap)；

public static AbsPersonaClient createLocalClient(Context c, String type, String actionRulesFile, String switchRulesFile, Map<String, IActionFactory> actionFactoryMap, PersonaClientListener listener)；
```

* **actionRulesFile**，请参照动作规则文档
* **switchRulesFile**，请参照动作切换规则文档
* **actionFactoryMap**，随后会有说明

### PersonaClient的注册和注销

* PersonaClient在创建的时候会自动注册到Persona中
* 在任何时候都可以通过PersonaClient.disconnect\(\)进行注销，并通过PersonaClient.connect\(\)进行重新注册
* PersonaClient的注销和重新注册的时机取决于PersonaClient自身的特性和产品需求，下面会举例说明

### PersonaClient: face和mini\_robot

一般地，Persona对注册的PersonaClient的类型和数量都不做限制，但目前只支持同时只有一个PersonaClient是激活状态。 
Persona中默认有对两种类型的PersonaClient的优先级管理，分别是face和mini\_robot，目前优先级规则只有一条： face的优先级高于mini\_robot。

##### 关于face和mini\_robot的功能定位

首先需要说明的是，这两种类型的PersonaClient并不是必需的，但是推荐使用这两种已有类型。另外，使用的时候，也不一定两种都要实现，可以按照产品需求选用。

* face的设计初衷是用于满足有图形显示需求的PersonaClient，而且它的生命周期是和场景生命周期挂钩的，即特定场景退出，进行注销，特定场景进入，重新注册。
* mini\_robot设计用于face处于非激活状态时对Persona指令进行反馈。mini\_robot从表现上看是一个背景PersonaClient，即从注册起，就一直存在，不会被注销。另外需要说明的是，mini\_robot是可以有图形显示的\(实现上一般通过WindowManager\)。

```java
//face
Map<String, IActionFactory> actionFactoryMap = new HashMap<>();
//insert ActionFactorys for face
AbsPersonaClient faceClient = PersonaClientFactory.createLocalClient(
                context,
                "face",
                "rules/action_build_rules.xml",
                "rules/action_switch_rules.xml",
                actionFactoryMap);

//mini_robot
Map<String, IActionFactory> actionFactoryMap = new HashMap<>();
//insert ActionFactorys for mini_robot
AbsPersonaClient faceClient = PersonaClientFactory.createLocalClient(
                context,
                "mini_robot",
                "rules/action_build_rules_mini.xml",
                "rules/action_switch_rules.xml",
                actionFactoryMap);
```

###IActionFactory
PersonaClient在构建时需要传入一个Map&lt;String, IActionFactory&gt;参数，该参数用于解析动作规则中输出节点的Action标签(即解析出对应的Action)。Map中的key即对应Action标签名，IActionFactory即对应的Action解析器。

```java
public interface IActionFactory {
    /**
     * 生成对应标签名的Action
     * @param attributes 动作规则中Action标签的所有属性及值
     * @return 动作规则中Action标签对应的Action
     */
    Action createAction(Map<String, Object> attributes);
}
```

####示例
IActionFacotry实现：
```java
package com.roobo.sample;

import android.content.Context;
import android.os.Handler;
import android.widget.FrameLayout;

import com.roobo.persona.action.Action;
import com.roobo.persona.action.builder.IActionFactory;

import java.util.Map;

/**
 * Created by march on 17-2-6.
 */

public class UiActionFactory implements IActionFactory {
    private Context mContext;
    private Handler mStateHandler;

    private FrameLayout mParent;

    public UiActionFactory(Context c, Handler stateHandler, FrameLayout parent) {
        mContext = c;
        mStateHandler = stateHandler;
        mParent = parent;
    }

    @Override
    public Action createAction(Map<String, Object> attributes) {
        return new UiAction(mContext, mStateHandler, mParent);
    }
}
```

PersonaClient创建：
```java
Map<String, IActionFactory> actionFactoryMap = new HashMap<>();
actionFactoryMap.put("ui", new UiActionFacotry(context, handler, parent));
AbsPersonaClient faceClient = PersonaClientFactory.createLocalClient(
                context,
                "face",
                "rules/action_build_rules.xml",
                "rules/action_switch_rules.xml",
                actionFactoryMap);
```

如上创建的PersonaClient说明，在动作规则文件中输出节点中Action标签名为ui的将使用UiActionFactory解析出对应的Action。



