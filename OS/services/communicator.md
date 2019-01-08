## Concepts
#### AIEvent 与 AICommand
RooboOS 中的消息处理就是 “将 AIEvent 处理转化为 AICommand” 的标准化（或者抽象化）过程，一组事件（AIEvent）就是一组输入信息，输入信息分为触发式的事件（即时有效，此次处理之后消失，我们称为 Trigger）以及粘性（sticky）的不会触发输出的事件（该事件一直存在，直到它的值变化，我们称之为State。每次处理 Trigger 时都会把系统内所有State一并考虑），一个 AI 命令（AICommand）就是针对系统当前的State和Trigger的响应。
#### Communicator 和 SceneHelper
RooboOS接收事件，输出命令。能够发送事件给系统或者从系统接收事件的单元，我们称之为模块。一个模块一定是一个进程。一个APK中可以包含多个模块。
为了让模块能够与系统进行通讯，也为了让一个进程能够作为一个模块参与整个系统的运作，需要挂载Communicator服务。
对于系统内的[服务](service.md)，使用Communicator。对于系统内的[场景](scene.md)，因为Communicator已经被包含在[场景服务](sceneservice.md)当中，使用[场景服务](sceneservice.md)即可。
## Communicator
#### AndroidManifest.xml中的声明
一个服务声明的例子如下：
```xml
<service
	android:name=".LocationModuleService"
	android:exported="true"
	android:process=":LOCATION">
	<meta-data
		android:name="ROOBO_MODULE_NAME"
		android:value="LOCATION" />
	<meta-data
		android:name="ROOBO_MODULE_TYPE"
		android:value="service" />
	<meta-data
		android:name="ROOBO_KEEP_ALIVE"
		android:value="true" />
</service>
```
上面的代码展示了在APK独立进程中声明服务的方法。  
ROOBO_MODULE_NAME 指定了服务的名称。ROOBO_MODULE_TYPE指定了服务模块的类型，ROOBO_KEEP_ALIVE声明是否要求对该进程进行保活。  
如果上述声明直接写在applicaition节点下，则会使用主进程作为模块进程。  
我们可以在一个APK中声明多个模块和服务，由于场景检测方面的限制，一个APK下只能有一个场景。
#### 初始化
通讯服务工具类（Communicator.java）提供三种初始化的方法：
```java
public static boolean initialize(Context context);

public static boolean initialize(Context context, IBinder binder);

public static boolean initialize(Context context, IBinder binder, ServiceConnectionListener serviceConnectionListener);
```
如果不指定binder和serviceConnectionListener, 该模块只能接收系统指令，不能发送事件。  
如果指定了binder，那么该模块可以向外提供服务。对应的，在AndroidManifest.xml中需要指定该服务的名称，同时声明模块类型为服务。  
serviceConnectionListener用于接收该模块与系统连接与断开的事件。当系统核心服务重启的时候，模块可能需要重新设置某些信息。  

#### 接收AI指令

初始化Communicator之后，如果想接收 AICommand 还需要设置对应的listener：
```java
public interface CommandListener {
        /**
     * @param action     命令动作
     * @param params     命令参数
     * @param suggestion 序列化的数据
     */
    void onCommand(String action, Bundle params, List<String> suggestion);
}
public class Communicator {
	public synchronized static void setCommandListener(CommandListener commandListener);
}
```
#### 发送事件
Communicator 类提供两种主动发送事件的方法，区别是每次发送一条事件还是多条事件。
```java
public class Event {
    public String key;
    public Serializable value;
    public boolean sticky;
}
public class Communicator {
	public static void postEvent(Event event);
	public static void postEvents(List<Event> events);
}
```
例如，当 GPS 模块发现地理位置变化时将经纬度通知给 RooboOS，这就是一个 State(location = XXX.XXX, XXX.XXX)：
```java
List<Event> events = new ArrayList<>();
events.add(new Event(KEY_LATITUDE, lat, true));
events.add(new Event(KEY_LONGITUDE, lon, true));
Communicator.postEvents(events);
```
当前系统已经进入打车场景，告知系统当前场景为打车场景，此信息就是一个 State（top.scene = Taxi）:
```java
Event event = new Event("top.scene", "Taxi", true);
Communicator.postEvents(event);
```
当用户对着麦克风说一句话时，ASR 处理后的语义信息就是一个 Trigger：
```java
Event event = new Event("asr.text", "我要去望京SOHO", false);
Communicator.postEvents(event);
```