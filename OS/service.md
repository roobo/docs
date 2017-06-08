## Concepts
service（服务）不同于 scene（场景），service 没有生命周期和相关的调度，它往往只是提供一项资源服务，或者只是一个设备的UserDriver（用户层驱动）。

例如机器人为了提供 “摸一下就有反馈” 的功能，就需要有 TouchSerivce 服务模块，当用户有触摸动作时，该服务模块应该承载从底层上来的按键反馈事件（Input event），也要向上层提供 onKeyEvent 事件回调。
## Tutorial
#### 服务声明
声明一个服务需要在 AndroidManifest.xml 中写入如下 meta-data 段：
```xml
<meta-data
	android:name="ROOBO_MODULE_NAME"
	android:value="TOUCH"/>
<meta-data
	android:name="ROOBO_MODULE_TYPE"
	android:value="service"/>
<meta-data
	android:name="ROOBO_KEEP_ALIVE"
	android:value="true"/>
```
这个模块名（ROOBO_MODULE_NAME）叫 TOUCH，模块类型（ROOBO_MODULE_TYPE）是 service。
#### 服务初始化
服务声明后需要在 Application.onCreate() 中尽量早的地方调用如下方法：
```java
class Communicator {
	...
	public static void initialize(Context context, IBinder binder);
	...
}
```
其中 context 建议传入 ApplicationContext，binder 就是该服务提供的 Binder 接口。当初始化时，系统将传过来的 Binder 接口保存在系统的 ServiceManager（服务管理器）中。

例如 Touch 服务提供 ITouch 的 Binder 接口，首先提供 aidl 文件：
```java
interface ITouch {
	void onTouchEvent(int eventCode, int action);
}
```
Touch 服务模块中实现接口：
```java
private static ITuch.Stub sBinder = new ITouch.Stub() {
	@Override
	public void onTouchEvent(int eventCode, int action) throws RemoteException {
		// todo server 端具体实现
	}
};
```
Application.onCreate() 中初始化操作：
```java
public class App extends Application {
    @Override
    public void onCreate() {
	    Communicator.initialize(this, sBinder.asBinder());
	}
}
```
#### 服务的使用
服务接口以 Map<ModuleName, IBinder> 的形式保存在 ServiceManager 中，我们可以通过 RooboServiceManager 接口类拿到指定服务接口来使用，例如 Touch 服务提供 ITouch 的 Binder 接口，如下代码段所示：
```java
private static ITouch getService(Context context) {
	if (context == null) {
		return null;
	}
	IBinder iBinder = RooboServiceManager.getService(context, <MODULE_NAME>); // 这里 <MODULE_NAME> 改成对应服务模块的模块名
	if (iBinder != null && iBinder.isBinderAlive()) {
		return ITouch.Stub.asInterface(iBinder);
	}
    return null;
}
```
一般来说，为了方便其他场景或者模块更方便的使用自己开发的服务，建议提供一个服务 SDK 供其他开发者使用，而不是直接使用提供的 Binder 接口。
