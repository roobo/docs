## Concepts
#### 场景调度
在 “场景” 章节我们已经说过，一个场景有三个重要回调：
```java
void onSwitchIn();
void onCommand(String action, Bundle data, Serializable suggestion);
void onSwitchOut();
```
当场景还不是顶级场景时，触发某场景的语义结果传过来后，系统将先调度启动目标场景并置为顶级场景，此时场景应用的 onSwitchIn 回调被调用，之后 onCommand 方法再被调用将语义结果传给场景；
当场景已经是顶级场景时，触发某场景的语义结果传过来后将直接调用 onCommand 方法传给场景；
当场景已经是顶级场景时，场景内部可以主动跳转至其他场景（一般来说，在一个场景下语义结果不会与其他场景有关系）。
注意：场景的 onSwitchIn、onCommand、onSwitchOut 函数均是运行在 UI 线程。
#### AIContext
场景可以给自己设置一个 AI 上下文，以给我们的 CloudAI 做辅助说明，虽然很多时候云端可以根据语义智能地切换上下文，但是在有用户其他交互特别是有屏幕的机器人上，用户的其他交互方式也会影响场景的切换，比如在我们即将上市的布丁豆机器人上，用户可以通过点击屏幕上的图片进入 “成语接龙” 场景，这时候云端是没有收到任何语义信息的，也不会有上下文切换，这时如果用户来了一句 “四面楚歌”，云端还以为你要聊历史呢。如果在进入 “成语接龙” 场景时在语义上传至云端时顺带一个上下文信息 “Idioms”，云端即可判断当前就在 “成语接龙” 场景，就可以正确的响应相对应的用户指令，在场景退出时，上下文信息会被清空，云端就会知道场景退出，之后的语义将与成语接龙无关。
## Tutorial
我们提供两个工具类，一个是给场景用的接口类 SceneHelper，一个是给服务用的场景变化监听类 SceneManager。
####  SceneHelper
```java
public class SceneHelper {
	// 场景初始化
	public synchronized static void initialize(Application application);
	// 判断模块是否已经初始化
	public static boolean isInitialized();
	// 监听场景回调接口
	public static void setEventListener(SceneEventListener eventListener);
	// 设置是否需要系统保活
	public static void setKeepAlive(boolean keepAlive);
	// 主动退出场景
	public static void switchOut();
	// 判断自己是否是顶级场景
	public static boolean isActive();
	// 主动启动并转到指定场景
	public static void startScene(String scene, String action, Bundle data);
	// 设置 AI 上下文
	public static void setContext(String context);
}
```
#### SceneManager
```java
public interface OnTopSceneChangedListener {
    void onSceneChanged(SceneRecord oldRecord, SceneRecord newRecord);
}

public class SceneManager {
	public void addOnTopSceneChangedListener(OnTopSceneChangedListener listener);
	public void removeOnTopSceneChangedListener(OnTopSceneChangedListener listener);
}
```