## Concepts
#### AIEvent 与 AICommand
RooboOS 中的消息处理就是 “将 AIEvent 处理转化为 AICommand” 的标准化（或者抽象化）过程，一个事件（AIEvent）就是一个输入信息，输入信息分为触发式的事件（一定会触发一个输出，我们称为 Trigger）以及粘性（sticky）的不会触发输出的事件（每次处理 Trigger 时都会把此类事件一并带上，我们称为 State），一个 AI 命令（AICommand）就是一个输出信息。
## Tutorial
#### 初始化
凡是想参与到系统的消息机制中去，都需要先初始化，通讯服务工具类（Communicator.java）提供初始化的方法：
```java
public class Communicator {
	public static void initialize(Context context);
}
```
想接收 AICommand 还需要设置监听器：
```java
public interface CommandListener {
    void onCommand(String action, Bundle params, Serializable suggestion);
}
public class Communicator {
	public synchronized static void setCommandListener(CommandListener commandListener);
}
```
#### 发送事件
Communicator 类提供两种主动发送事件的方法，这种发送事件的方式也可以被称为用户层事件驱动，也可以称为事件抽象层。
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

#### 举例说明
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
系统将所有 State 和此 Trigger 一并处理，输出一个 AICommand 发给当前场景（Taxi），场景内接收 AICommand：
```java
Communicator.setCommandListener(new CommandListener() {
	void onCommand(String action, Bundle params, Serializable suggestion) {
		if ("Reserve".equals(action)) { // Reserve 是在 ROS 云端配置好的 action
			String dest = params.getString("dest");
			// todo
		}
	}
});
```