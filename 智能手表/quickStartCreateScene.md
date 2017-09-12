### 场景是什么
Scene（场景），在产品层面上是体现一个机器人交互能力的直接途径，是体现用户体验质量的直接载体，是用户的直接交互对象；同时在技术层面上是AI消息传递机制中的module（基本模块），是AICommand发送的目标\(target\)，场景作为与用户直接交互的对象，拥有自己的生命周期，开发者用户需要严格按照生命周期来开发自己的程序。
在已经部署好的工程中加入自定义场景,需要经过如下几个步骤

#### 创建module

在scenes目录下创建自己的Module 如：　Pudding

![](/OS/assets/quick_start_6.png)

#### 修改build.gradle

```java
apply plugin: 'com.android.application'

android {
    apply from: "${rootProject.ext.app_common}"
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile project(':interfaces:SceneSDK')
}
```

添加对开发所需的依赖包

```java
compile project(':interfaces:SceneSDK')
```

为方便管理，建议应用统一的打包配置

```java
apply from: "${rootProject.ext.app_common}"
```

#### 修改AndroidManifest.xml

在application 中添加如下内容：

```xml
<service
            android:name="com.roobo.core.communication.DefaultService"
            android:exported="true" />

<meta-data
            android:name="ROOBO_MODULE_NAME"
            android:value="Pudding" />

 <meta-data
            android:name="ROOBO_MODULE_TYPE"
            android:value="scene"/>
```

  **DefaultService**
  保证系统能够跟你建立通讯

  **ROOBO\_MODULE\_NAME**

   代表该模块的名字，必须声明，同一系统上的**模块名不能重复**

  **ROOBO\_MODULE\_TYPE**

   代表该模块的类型，可选声明，值有三种，scene、service和other，默认不写该项指的是other，其中scene表示该模块是一个场景，service表示该模块是一个服务，其他值表示仅是一个普通模块快速接入指南中仅介绍scene ．

#### 在ROS.AI端配置创建场景及语义

具体在ROS.AI端配置场景及相关语义的方法请参照　[ROS.AI开发文档](http://ros.ai)

![](/OS/assets/quick_start_7.png)   
 ![](/OS/assets/quick_start_8.png)

#### 接收Command

在ROS.AI端配置完成服务后，输入对应的语义，我们的场景就能接收到对应的Command .不过在此之前我们还需要做以下操作．

**场景初始化**

建立一个自己的Application，并在AndroidManifest.xml 中配置使用．  
作为一个scene\(场景\)，需要使用SceneHelper.initialize\(Application app\)方法进行初始化操作，该方法尽量在Application.onCreate\(\)的时候尽可能早的执行。

**设置EventListener**

场景生命周期函数有三个，通过SceneHelper.setEventListener\(SceneEventListener listener\)来注册生命周期函数回调．

#### 区分意图

根据再ROS.AI端的配置，我们可以通过回调函数里的数据区分出用户的意图．然后做出对应的回应．快速上手中使用action , 其余参数请参考详细文档．

**注意**  
语义解析需要有上下文，在ROS.AI配置是选填的　，为了更精确识别语义，如果在ROS.AI配置时语义设置了上下文，　那在我们的场景时，也要设置上下文．建议同一个场景用同一上下文．

如：

```java
public class MyApplication extends Application {
    private static final String TAG = "Pudding";

    @Override
    public void onCreate() {
        super.onCreate();
        SceneHelper.initialize(this);
        /**　设置场景上下文 **/
        SceneHelper.setContext("pudding");
        SceneHelper.setEventListener(new SceneEventListener() {
            /** 场景切入时回调 **/
            @Override
            public void onSwitchIn(String action, Bundle params, Serializable suggestion) {
                super.onSwitchIn(action, params, suggestion);
                Log.d(TAG, "onSwitchIn called " + action);
                Intent intent = new Intent(MyApplication.this, MainActivity.class);
                intent.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
                startActivity(intent);
            }

            /**场景切出有四种情况：主动切出、被唤醒词切出、被切入其他场景、进程异常退出，前三种，都会执行 onSwitchOut 回调，
             * 一般来说需要在该回调中做一些资源释放的工作。**/
            @Override
            public void onSwitchOut() {
                super.onSwitchOut();
                Log.d(TAG, "onSwitchOut called ");
            }

            /**
             * onCommand：进入场景(onSwitchIn)后，只需在onCommand中接收消息进行一系列操作就可以了；
             * @param action 对应 Entry、Quit、Echo 这几个自定义行为
             * @param params 额外参数传递
             * @param suggestion 额外参数传递
             */
            @Override
            public void onCommand(String action, Bundle params, Serializable suggestion) {
                super.onCommand(action, params, suggestion);
                Log.d(TAG, "onCommand called " + action);
                if (action.equals("ask")) {
                    PersonaPlayer.playTTS(MyApplication.this, "主人我在这里，欢迎来到自定义布丁场景");
                } else if (action.equals("eat")) {
                    PersonaPlayer.playTTS(MyApplication.this, "哈哈，我是布丁机器人，不能吃的哦．");
                } else if (action.equals("praise")) {
                    PersonaPlayer.playTTS(MyApplication.this, "好吧，谢谢主人对我的赞美，我会告诉别人我很高兴的．");
                }

            }
        });
    }
}
```

#### 修改global\_config

开发包默认的**device.production**　已经盖我们刚自定义的场景，如果后续有了自己的ROS.AI的后台就所以必须将该值修改下．  
在sdcard/ros/configure/创建　**global\_config.xml**　写入：

```xml
<?xml version="1.0" encoding="utf-8"?>
<config>
    <item key="device.production" type="string" value="test"/>
</config>
```

我再ROS.AI创建的产品就是　＂test＂ , 如果你的不是请填入你的ROS.AI的产品名

#### 修改更换sn号

产品的名称已经修改了,也需要对应的修改sn号.  
打开/sdcard/下 sn 文件,写入对应的数据,如我我们刚开发的场景

```
sn=1110000000101063
key=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDvFA5QnWpzrss9bKqukAuOp5uqQ2pwQBZGUb4Cg/mX4gDB0JWaWSbggzli/XNbrI3ChOO9SsFiF8JM7dLB+efBAlDuphz35mgAY71N/bfzjnE/5cltvH1VuNeV5Lz8zFm6sJlO9H9ZjLDpJYeXL0XHTfY/oTM3hDgn/+W/3kWY8wIDAQAB
```

#### 安装与调试

将该场景安装到设备上.
此时一个新的场景已经开发完成了,但是目前还有处罚这个场景的触发点.也就是不会数据传递给这个我们新开发好的场景.因为所有的数据都转发给了 "SHOW_MSG" 这个场景. 快速上手-拆分场景数据会详细介绍.

