#PersonaPlayer

Persona除了接收AI指令外，也向场景提供相应的接口，使场景可以直接向Persona请求特定的服务。

目前提供的服务有两类：
* 说话(playTTS)
* 执行特定Action(playAction)

###API
PersonaPlayer对外提供的都是静态接口。

```java
/**
 * 说一段话
 * @param context
 * @param text 要说的字符串
 */
public static void playTTS(Context context, String text);

/**
 * 说一段话，并设置状态监听
 * @param context
 * @param text 要说的字符串
 * @param listener 状态监听器
 */
public static void playTTS(Context context, String text, OnPlayerStateChangeListener listener);

/**
 * 执行特定的Action
 * @param context
 * @param actionId Action规则中指定的action_id
 * @param params Action附带的参数
 * @param suggestion Action附带的参数
 * @param listener 状态监听器
 */
public static void playAction(Context context, String actionId, Bundle params, Serializable suggestion, OnPlayerStateChangeListener listener)

public interface OnPlayerStateChangeListener {
    /**
     * tts开始或者Action开始执行
     */
    void onActionStarted();

    /**
     * tts结束或者Action执行完毕
     */
    void onActionFinished();
}
```



