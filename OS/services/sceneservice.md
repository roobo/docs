## 场景接口
#### 场景调度
场景调度依循两个维度进行，GUI和VUI。  
如果某个时刻有UI在顶层显示，则对应的场景成为顶级场景。  
顶级场景之外，场景栈中的顺序按照“最近交互”原则排列。  
场景调度在应用程序内体现为一系列回调函数：
```java
    /**
     * 场景退出回调
     */
    public void onSwitchOut() {}

    /**
     * 场景进入回调
     *
     * @param flags {@link SceneHelper#SCENE_ATTR_OVERLAP}, {@link SceneHelper#SCENE_ATTR_NO_ANIMATION}, {@link SceneHelper#SCENE_ATTR_CONTINUOUS},
     */
    public void onSwitchIn(int flags) {}

    /**
     * 场景事件回调
     *
     * @param action     事件命令词
     * @param params     命令参数
     * @param suggestion 命令其它参数
     */
    public void onCommand(String action, Bundle params, List<String> suggestion) {}

    /**
     * 场景pause回调
     */
    public void onPause() {}

    /**
     * 场景resume回调
     */
    public void onResume() {}

    /**
     * 场景pause时，保存数据回调
     *
     * @param data
     */
    public void onSaveSceneData(Bundle data) {}

    /**
     * 场景resume时，还原数据回调
     *
     * @param data
     */
    public void onRestoreSceneData(Bundle data) {}
```
##### 场景切入
当场景不在场景栈时，如果用户发起了对应该场景的语音请求，这个场景会被放入场景栈，并且位于场景栈的第二层。这个时候onSwitchIn()会被调用。
##### 接收指令
随后，onCommand()会被调用，将用户语音的意图发送给场景。
##### 成为顶级场景
在处理用户意图的过程中，如果应用程序启动了新的Activity或者window，将自己的UI放到了UI层级的最顶层，该场景会被置为顶级场景。此时onResume()会被调用。  
如果在处理用户意图的过程中并没有UI层级的变动 —— 例如，音乐后台播放的时候，用户发出播控指令，此时并不需要将音乐UI显示出来 —— 那么该场景不会成为顶级场景，也不会收到onResume()回调。  
顶级场景在申请某些focus的时候具有比非顶级场景更高的优先级，具体哪些focus依赖于平台配置。
##### 非顶级场景
如果一个顶级场景隐藏了自己的UI，或者另外一个场景显示了新的UI，此时原先的顶级场景会被放到场景栈的第二层，同时收到onPause()回调。
UI显示层级最高的场景将占据顶级场景的位置。  
>##### 注意
>场景的 onSwitchIn、onCommand、onSwitchOut 函数均是运行在 UI 线程。
####  SceneHelper
##### 接口说明
```java
/**
 * 初始化场景
 *
 * @param application {@link Application}
 * @return true，初始化成功，false，初始化失败SceneServiceInterface
 */
public synchronized static boolean initialize(Application application);


/**
 * 是否已经初始化
 *
 * @return true，已经初始化，false，没有初始化过
 */
public static boolean isInitialized();


/**
 * 设置场景事件监听器.
 * <p>
 * 通过该监听器获取系统分发的场景事件
 *
 * @param eventListener {@link SceneEventListener}
 */
public static void setEventListener(SceneEventListener eventListener);

/**
 * 场景是否保活
 *
 * @param keepAlive true，保活
 */
public static void setKeepAlive(boolean keepAlive);

/**
 * 查询场景是否是顶级场景
 *
 * @return true/false
 */
public static boolean isActive();

/**
 * 退出场景.
 * <p>
 * 场景主动退出时，一定要调用该方法。被动的场景调动，不需要
 */
public static void switchOut();

/**
 * 设置系统当前场景名称
 *
 * @param service 场景名
 */
public static void setService(String service);

/**
 * 设置语义上下文
 *
 * @param context 当前上下文
 */
public static void setContext(String context);

public static String getContext();

public static void addContext(String context);

public static void removeContext(String context);

/**
 * 设置上下文参数
 *
 * @param params 上下文参数
 */
public static void setParams(Map<String, Serializable> params);
```
##### 初始化
调用SceneHelper的initialize可是初始化场景服务并且在系统内部注册该场景。场景的名称在AndroidManifest.xml中声明。

#### 设置上下文
场景内的状态成为上下文。很多时候云端可以根据语义智能地切换上下文，但是在有用户其他交互特别是有屏幕的智能设备上，用户的其他交互方式也会影响场景的切换，用户可以通过GUI操作完成一些业务流程，此时云端没有收到任何语义信息，也不会有上下文切换。如果用户发起语音指令，云端可能会因为错误的上下文导致语义解析出错。  
为了能够与云端同步上下文信息，场景可以调用接口设置当前的上下文。OS中的上下文是分层的，最新添加的上下文会被排在最前面。  
除了上下文之外，设备GUI操作产生的槽位信息也需要同步到云端。可以通过调用setParams()上传槽位。

## 场景管理器
除了SceneHelper之外，我们还提供场景变化监听类 SceneManager。
### 接口说明
```java
public interface OnTopSceneChangedListener {
    void onSceneChanged(SceneRecord oldRecord, SceneRecord newRecord);
}

public class SceneManager {
	public void addOnTopSceneChangedListener(OnTopSceneChangedListener listener);
	public void removeOnTopSceneChangedListener(OnTopSceneChangedListener listener);
}
```
场景管理器提供接口监测系统的场景变化，注册listener即可收到回调。