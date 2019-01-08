## Module
在系统中，Module（模块）是消息通讯的基本单位，所有想参与到消息通讯的应用都需要声明为一个 module 并进行初始化。
#### 分类
模块有三种：场景、服务与其他。
#### 场景
场景是和用户直接交互的程序，它将接收用户语义的AI返回结果作出一系列的响应（如 GUI、Motion、TTS 等），当收到一条发给场景A的消息时，系统将拉起场景A，并将A置为顶级场景，当场景B取代A成为顶级场景或者场景A自己退出时，场景A将收到切出场景的回调，场景可以有UI也可以没有UI。例如翻译场景，；
#### 服务
服务能够对外暴露一个 binder 接口，供其他模块使用，
#### 其他
其他模块指的就是既不是场景也不是服务的普通模块，它也可以接收消息做出自己的响应，但既不能作为一个场景能够拥有资源，也不能对外提供服务接口，最简单的例子就是 Location 模块，该模块将20秒查询一次地理位置信息并上报给系统。
#### 声明与初始化
无论是什么样的模块，必须进行声明与初始化，该模块才能参与到系统通信机制中，声明方式是在 AndroidManifest.xml 中写入如下 meta-data 段：
```xml
<meta-data
    android:name="ROOBO_MODULE_NAME"
    android:value="LOCATION" />
```
初始化方式是在 Application.onCreate() 中尽量早的写入如下代码段：
```java
Communicator.initialize(this);//如果不需要对外提供IBinder，使用此方法初始化
```
#### 保活机制
KEEP_ALIVE 是模块的一种属性，拥有 KEEP_ALIVE 属性的模块进程在 attach 到系统中后，系统将 “监听” 该进程，模块进程异常退出后会重新再次将其启动，通常拥有后台服务的模块会添加此属性。
添加此属性的方式是在 AndroidManifest.xml 中写入如下 meta-data 段：
```xml15
<meta-data
    android:name="ROOBO_KEEP_ALIVE"
    android:value="true"/>
```
#### 自启机制
当系统启动时，将会查询production_service.xml 中配置的自启项目，如下所示：
``` xml
<?xml version="1.0" encoding="utf-8"?>
<config>
    <item name="ASR" package="com.roobo.asr" type="service"/>
    <item name="LOCATION" package="com.roobo.location" type="service"/>
    <item name="ThemeManagerService" package="com.roobo.theme.service" type="service"/>
</config>
```
production_service.xml可自行编辑。
其中 name 代表模块名，package 代表模块的包名，type表示模块的类型，有三种值：scene、service、module，分别代表场景、服务和其他模块。

系统会在启动时会根据name（模块名）去查找清单文件中包含key为ROOBO_MODULE_NAME且value和name相等的meta-data标签的组件。

1，如果该meta-data标签位于application标签下，则会尝试启动该模块下的com.roobo.core.communication.DefaultService，DefaultService类已经在SceneSDK中包含，需要在清单文件中声明DefaultService。

2，如果该meta-data标签位于Service标签下，则会尝试启动该Service。

## Communicator和SceneHelper
模块和场景通讯机制是整个系统运作的核心。作为模块的基础工具类，提供三种和通讯相关的收发功能。  

#### 发送消息（AIEvent）
AIEvent 可以是一个输入设备的信息，可以是某个功能的状态，也可以是某个模块发出的消息，具体 AIEvent 的用法与规则详见 “roobo OS 通讯方式”。
Communicator 类中发送消息方式如下两个函数：
```java
public class Event {
    public String key;
    public Object value;
    public boolean sticky;
}
public static void postEvents(List<Event> events);
public static void postEvent(Event event);
```
#### 接收消息（AICommand）
AICommand 是发送给目标模块的最终格式化消息，一个模块若想要接收 AICommand 就需要注册监听回调，Communicator 类中监听注册的方法是 setCommandListener：
```java
public static void setCommandListener(CommandListener commandListener);

public interface CommandListener {
    /**
     * @param action     命令动作
     * @param params     命令参数
     * @param suggestion 云端返回的数据
     */
    void onCommand(String action, Bundle params, List<String> suggestion);
}
```
更多细节参考[通讯服务](./services/communicator.md)和[场景服务](./services/sceneservice.md)
