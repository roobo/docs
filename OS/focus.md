## 背景
智能手机上提供了一系列与用户交互相关的 “设备” 资源，触摸屏、虚拟按键、麦克风、摄像头都属于输入设备，LED灯、MediaPlayer 属于输出设备，我们的手机上总是有多个应用程序同时在运行，有时候手机上允许它们同时控制同一种设备：比如可以通过多个 MediaPlayer 实例播放声音，但也有一些设备如果所有应用都有权利直接控制那就乱套了：比如只有当前的界面才能响应触摸屏操作，比如手机上有两个应用 A、B 都会响应 back 虚拟按键，如果 A 是当前可见应用时用户按 back 键，B 就不该响应，又比如 A、B 若同时使用 Camera，并且摄像头的参数还不一样，那么 CameraService 就不知道以谁的为准。
 
在机器人上，各种设备的互斥访问也是必要的。例如某开发者开发的 A 场景在不是当前场景时突然来一句广告词以 tts 或者 MediaPlayer 的方式播放出来，这是绝对不允许的。
## Concepts
#### 设备
在本文中 “设备” 一词指的是提供资源输入、控制输出的虚拟模块，也可以称为与具体硬件设备直接通信或者间接通信的用户层驱动。
#### Focus
在 RooboOS 中我们引入 focus 的概念，以达到设备权限控制的目的，当某模块要使用某种需要 focus 的设备时，需要先申请 Focus，若申请成功我们就称该模块有这种设备的 Focus。例如 Launcher 模块需要接收 Touch 事件（以在用户触摸不同的机器人部位时做出不同的表情），先主动申请 TouchService 的 focus，若申请成功，则之后 Launcher 将持续收到 Touch 事件直到主动释放 Focus，若申请失败则不会收到。当 “打鼓游戏” 场景在 Launcher 申请成功后也申请 Touch 设备的 focus 并成功时，Launcher 模块的 Touch focus 将被 “抢占”，被迫自动释放。
##### requestFocus
申请某种设备的 focus，这种行为我们称为 requestFocus，无论是否申请成功系统中会将申请记录保存在一个优先级队列中，若申请者所在 group 的规则有优先级属性，则组内所有申请者的优先级都是一样的。同一优先级的申请记录会互相覆盖。
##### releaseFocus
释放某种设备的 focus，这种行为我们称为 releaseFocus，释放 focus 时，优先级队列中对应的申请记录也一并删除，之后 focus 将落给优先级队列的最高优先级申请者。
#### Focus Group
但是并不是每次申请成功时都会导致另外一个申请者被 “抢占”，有些 Focus 是可以共有的，这里我们引入 Group 的概念，每一种 focus 的每个 Group 内的模块是互相抢占的，但是不同 Group 的模块的 focus 可以共同拥有。比如当前场景一定会有 persona（播放表情、动作、TTS）的 focus ，但是系统模块同样会在收到 QQ 消息通知时播放相关表情和 TTS，这时场景和系统模块就是在不同的 Group 中同时拥有 persona 的 focus。
#### 优先级
在系统中，优先级是一个 Float 值，它代表了同一个 focus group 中不同模块申请的优先级，高优先级（或平等优先级）能抢占低优先级，低优先级无法抢占高优先级，高优先级模块释放 focus 后低优先级申请者将自动获取 focus（前提是有申请记录）。
 
假如我们有网络电话场景，由于在电话过程中我们不希望其他模块有机会播放表情和TTS（甚至会禁用 AudioRecorder），网络电话场景会申请 persona 的 focus，我们还有个 SYSTEM 模块，在收到消息通知时它会主动播放TTS，但是在网络电话场景下，SYSTEM 模块也不能擅自播放 TTS。这时规则就应该是 网络电话场景与 SYSTEM 模块在同一个 focus group 中，且网络电话场景的优先级高于SYSTEM模块，在网络电话场景下，SYSTEM 模块申请 persona 的 focus 会失败，当网络电话场景退出时，SYSTEM 将自动获取到 focus。
#### Fallback
很多时候优先级能够解决我们的问题，但是我们仍然提供一个最低优先级的概念 - fallback，每一种 focus 规则的 group 中都有一个 fallback，fallback 一般来说是一个模块，当该 group 中有其他模块申请了 focus，fallback 模块若已经得到focus，则将失去 focus，若没有得到focus，申请focus也会失败，但申请记录会记录在优先级队列中，当其他模块释放了 focus，有申请记录的fallback模块将自动获取focus。
## Tutorial
#### 规则
一个模块是否能申请成功是按 Focus 规则来的， 也就是 focus_array.xml 规则文件，在 Configure 模块中，可以修改这个文件。focus_array.xml 对应了所有设备的 focus 申请规则，它规定了哪些模块在哪些情况下能够申请成功，如下代码段展示了 persona（情绪、动作、TTS）的 focus 规则：
```xml
<?xml version="1.0" encoding="utf-8"?>
<focus-array>
    ...
    <focus name="persona">
        <group>
            <list>
                <item>
                    <who>scenes</who>
                    <acquire>top</acquire>
                    <release>out</release>
                </item>
            </list>
            <fallback>none</fallback>
        </group>
        <group>
            <list>
                <item>
                    <who>SYSTEM</who>
                    <acquire>any</acquire>
                    <release>none</release>
                </item>
            </list>
            <fallback>none</fallback>
        </group>
    </focus>
    ...
</focus-array>
```
规则文件以 &lt;focus-array&gt; 为根节点，每种设备的 Focus 规则都以 &lt;focus&gt; 为根节点，focus 节点有一个属性 name 代表该种设备的名字，focus 的名字不能重复定义。focus 子节点为 &lt;group&gt;，可以有多个，每一个 &lt;group&gt; 中包含一个 &lt;list&gt;（也可以是优先级队列 &lt;pri-list&gt;）和一个 &lt;fallback&gt;，每一个 &lt;list&gt; 中包含若干个 &lt;item&gt;，每个 item 都代表一个模块或者模块集合的规则。
##### item
每一个 &lt;item&gt; 都有三个子节点，分别是 &lt;who&gt;、&lt;acquire&gt;、&lt;release&gt;（简称 “war”），who 代表该项规则的适用模块，可以是任何一个模块的模块名，也可以是 scenes，代表所有场景，acquire 代表该模块在什么时候能够成功申请到 focus，该值为 top 代表该模块是场景且是顶级场景时才能申请到此设备的 focus，release 代表该模块在什么时候能会被迫释放 focus，该值为 out 代表该模块是场景且场景退出时将自动释放 focus。
##### 规则关键字
目前有三个关键字：scenes、any、none、top、out
 
    scenes - 用于 who 标签中，代表该模块是场景且是顶级场景时才能申请到此 focus
    any - 一般用于 acquire 标签中，代表该模块在任何情况下都能抢占此 focus
    none - 默认填充值，一般用于 release 标签中，代表该模块在任何情况下都不会自动释放此 focus（除了被抢占）
    top - 一般用于 acquire 标签中，代表该模块在顶级场景时才能抢占此 focus
    out - 一般用于 release 标签中，代表该模块在场景退出时自动释放 focus
 
#### FocusManager
系统提供 申请 focus、释放 focus、查验是否有 focus 以及注册 focus 变化监听回调的接口：
```java
public interface OnModuleFocusChangedListener {
    // 有 focus 申请成功时的变化回调
    void onFocusWin(String focusName, String moduleName);
    // 有 focus 释放时的变化回调
    void onFocusLost(String focusName, String moduleName);
}
 
public class FocusManager {
 
    public static FocusManager getInstance(Context context) {
        ...// 单例
    }
    // 申请focus
    public boolean requestFocus(String focusName);
    // 释放 focus
    public boolean releaseFocus(String focusName);
    // 判断某进程是否有指定 focus
    public boolean hasFocus(int pid, String focusName);
    // 查询有指定 focus 的所有进程
    public int[] getCurrentFocus(String focusName);
    /** 监听指定模块指定focus的变化
     * focusName - 要监听的 focus，可以为 null，传 null 则表示监听所有 focus 变化，focusName 不可与 moduleName 同时为 null
     * 
    **/
    public void addOnFocusChangedListener(String focusName, String moduleName, 
                        OnModuleFocusChangedListener listener);
    // 移除指定模块指定focus的变化监听器
    public void removeOnFocusChangedListener(String focusName, String moduleName, 
                        OnModuleFocusChangedListener listener);
}
```
#### service 端
一般来说 service 端才是设备的提供者，也可以称一个 service 是用户层驱动，对于输出、输入两种设备，我们希望能提供不同的实现方案：
##### 输入设备
比如 touch、camera、AudioRecorder 等，一般会对外提供注册数据回调的方法，如下代码为 TouchService 的注册回调的方法：
```java
// aidl 文件 - ITouchService.aidl
interface ITouchService {
    void registerTouchListener(in ITouchListener listener);
    void unregisterTouchListener(in ITouchListener listener);
}
// aidl 文件 - ITouchListener.aidl
interface ITouchListener {
    void onKeyEvent(in RooboKeyEvent event);
}
 
public class TouchService extends ITouchService.Stub {
    @Override
    public void registerTouchListener(ITouchListener listener) throws RemoteException {
        if (null == listener) {
            return;
        }
        // todo 将 listener 保存在一个 map<pid,listener> 中
        map.put(getCallingPid(), listener);
    }
    @Override
    public void unregisterTouchListener(ITouchListener listener) throws RemoteException {
        if (null == listener) {
            return;
        }
        // todo 将 listener 从 map 中移除
        map.remove(getCallingPid());
    }
    public void triggerTouchEvent(RooboKeyEvent event) {
        int pids[] = FocusManager.getInstance(App.mApp).getCurrentFocus("touch");
        for(int pid : pids) {
            // 查询 pid 对应的 ITouchListener 
            ITouchListener listener = map.get(pid);
            if (null != listener) {
                listener.onKeyEvent(event)
            }
        }
    }
}
```
有时候输入设备需要监听 focus 的变化而做一些资源回收的工作，此时需要使用 addOnFocusChangedListener 接口，例如 TouchService：
```java
FocusManager.getInstance(context).addOnFocusChangedListener("touch", null, 
        new OnModuleFocusChangedListener() {
            @Override
            void onFocusWin(String focusName, String moduleName) {
                ... // 开始接收 touch event
            }
            @Override
            void onFocusLost(String focusName, String moduleName) {
                int[] pids = FocusManager.getInstance(context).getCurrentFocus(String focusName);
                if (null == pids || 0 == pids.length) {
                    ... // 停止接收 touch event
                }
            }
        });
```
##### 输出设备
比如 TTS、MediaPlayer 等，一般会在控制接口实现端判断调用者是否有 foucus，如下代码所示为 persona 播放 tts 的接口：
```java
public class PersonaPlayerService extends IPersonaPlayer.Stub {
    @Override
    public String playTTS(String text) throws RemoteException {
        if (!FocusManager.getInstance(mContext).hasFocus(getCallingPid(), "persona")) {
            OSDebug.log(TAG, "[playTTS]: 没有persona-focus");
            return null;
        }
        ... // 播放 tts
    }
}
```
#### focus 申请者 - client 端
一般来说，设备服务开发者会提供 client 端使用的接口，而在接口中帮你做了申请 focus 的步骤，client 端只需去用接口就够了，比如 Persona 提供的接口类 PersonaPlayer：
```java
public class PersonaPlayer {
    // 获取 Persona 服务模块提供的 Binder 接口 IPersonaPlayer
    private static IPersonaPlayer getService(Context context) {
        if (context == null) {
            return null;
        }
        IBinder iBinder = RooboServiceManager.getService(context, ACTION_PLAYER);
        if (iBinder != null && iBinder.isBinderAlive()) {
            IPersonaPlayer mService = IPersonaPlayer.Stub.asInterface(iBinder);
            try {
                mService.setCallback(playerCallback);
                return mService;
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        return null;
    }
 
    public static void playTTS(Context context, String text) {
        if (!FocusManager.getInstance(context).requestFocus("persona")) {
            OSDebug.log(TAG, "request focus persona failed, 无法播放tts");
        }
        IPersonaPlayer service = getService(context);
        if (service != null) {
            ... // 调用 aidl 接口
        }
    }
}
```
但如果设备开发方没有提供这些接口类，那么就只能 client 端自己实现上述代码了。
#### 线程安全
FocusManager 相关接口均是线程安全的，当模块 A 抢占了模块 B 的 focus 时，focus 变化回调接口 onFocusLost(B) 和 onFocusWin(A) 将是按顺序同步执行的，顺序为 onFocusLost(B) -> onFocusWin(A) -> requestFocus返回，我们希望在 focus 变化回调接口中的工作也是同步调用的，不然会引起资源释放时机延后导致的异常。