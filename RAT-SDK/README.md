RAT-SDK 开发指南v1.0.0
==

### 目录

[1.概述](#概述)

[2.使用说明](#使用说明)
* [2.1 准备](#准备)
* [2.2 主要流程](#主要流程)
* [2.3 使用步骤](#使用步骤)

[3.错误码对应表](#错误码对应表)

[4.支持的语言列表](#支持的语言列表)

### 概述
RAT-SDK是运行在Android平台，旨在为用户提供在线语音听写、离线语句识别、唤醒及离线语音合成的能力，目前支持语言请参见[支持的语言](#支持的语言列表)。

### 使用说明
#### 准备
 1. 账号申请，账号通常包括appID，publicKey，账号注意妥善保管。
 2. SDK及demo获取，目前SDK是以aar的形式提供，IDE需要用AndroidStudio。
 3. 对应语种的资源，每个语言包含对应的离线识别、TTS合成的模型文件。

#### 主要流程
SDK主要流程如下：

![](/VoiceService-SDK/assets/workflow.png)

#### 使用步骤
1. 配置编译环境，将SDK的aar文件放入业务Module的libs文件夹下，并且配置编译选项
``` java
    repositories {
        flatDir { dirs 'libs' }
    }
    dependencies {
        compile(name:'rat-release-1.0.2-online',ext:'aar')
    }
```
   将资源拷入业务Module的assets下，子目录和资源的名称不要改变。如下图所示：
   ![](/RAT-SDK/assets/offlineRes.png)
   
2. 初始化
    
    2.1. 鉴权，调用SDK鉴权接口联网鉴权，鉴权成功后才能使用SDK的能力。在第一次没有鉴权可以短暂使用离线能力。示例代码如下：
    
 ``` java
 RAuth auth = new RAuth(getApplicationContext());
 auth.auth(appId, publicKey, new RAuthResultListener() {
     @Override
     public void onSucess() {
     }
     @Override
     public void onFail(final RError error) {
     }
 );
 ```
    2.2. 在线听写、离线语句识别、唤醒初始化。在使用识别前一定要全包创建全局RooboUtility 对象，改类主要设置一些配置。如果是使用Android的标准AudioRecorder采集音频数据，则在startWork后会在其内部创建Recorder。示例代码如下：
     
 ``` java
 RooboUtility utility = RooboUtility.createUtility();
 utility.setParams(Parameter.ENDPOINT_TIME, String.valueOf(5000));
 utility.setParams(Parameter.ABSOLUTE_THRESHOLD,"-2600");
 utility.setParams(Parameter.SENSITIVITY,"30");
 utility.setParams(Parameter.T_SILENCE,"200");
 utility.initGrammar("offline-"+UserInfo.LANGUAGE.language());
 ···
 utility.startWork(getApplicationContext(), UserInfo.LANGUAGE, 0);
 utility.setVolumeListener(new VolumeChangeListener() {
        @Override
        public void onVolumeChange(int volume) {
           
        }
 });
 ```
>NOTE:我们支持用户自己开启AudioRecorder，需要在utility.startWork时最后一个参数设置为-1，并将原始音频数据通过utility的writePcm方法写入引擎。确保音频数据是单声道，采样率16000Hz，数据位深16bit。

3. 在线听写
初始化成功后可以使用在线听写，示例代码如下：
``` java
RooboCloudRecognizer mRecognizer = RooboCloudRecognizer.createRecognizer();
mRecognizer.setLanguage(UserInfo.LANGUAGE);
mRecognizer.startRecognize(new RecognizeListener() {
            @Override
            public void onResult(final String json) {
            }

            @Override
            public void onError(final String json) {
            }
        });
```

4. 离线语句识别、唤醒，离线语句和唤醒需要使用者提供离线词句及唤醒词，我们会将使用者的离线语句需求编译成引擎的语法文件提供给使用者，其中引擎会默认加载offline-开头的文法文件。示例代码如下：
``` java
RooboLocalRecognizer mRecognizer = RooboLocalRecognizer.createRecognizer(getApplicationContext());
mRecognizer.startRecognize(new RecognizeListener() {
            @Override
            public void onResult(final String json) {
            }

            @Override
            public void onError(String json) {
            }
});

RooboWakeuper mWakeuper = RooboWakeuper.createWakeuper();
mWakeuper.startWakeUp(new RecognizeListener() {
          @Override
          public void onResult(final String json) {
          }
          @Override
          public void onError(String json) {
          }
});
```

5. 离线TTS，使用时需要设置Speaker的名称，改名称可以从我们提供资源中的config.xml中获取。示例代码如下：
``` java
RTTSPlayer tts = RTTSPlayer.createPlayer(getApplicationContext(), null, null);
tts.setSpeaker(speakerName);
nt.speak("你好",new TtsListener(){

                            @Override
                            public void onSpeakBegin() {
                            }

                            @Override
                            public void onCompleted() {
                            }
          });
```

### 错误码对应表

error code | error des
------------ | ---------------------------------------------------------------
-412 | appId授权的设备数已经超出限额
-411 | appId公钥过期
-410 | 公私钥校验检查失败
-1000 | 权限校验失败
-1001 | 网络错误
100 | 无本地识别权限
101 | 无本地唤醒权限
102 | 无在线识别权限
103 | 连接错误，请检查系统时间或者网络
104 | 你好像没有说话

### 支持的语言列表
>如需要不在下述列表的语言，请与我们联系。

US English
Spanish(LatAM)
French for Canada
Portuguese for Brazil
Russian
Spanish(Spain)
English for GB
French for France
German
Danish
Catalan
Italian
Portuguese for Portugal
Dutch
Mandarin
Cantonese Simplified
Cantonese Traditional
Mandarin(Taiwan)
Korean
Japanese
English for Australia
English for India
Hindi
Arabic
Polish
Thai
Turkish
