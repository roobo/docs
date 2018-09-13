README
=

### 目录
[*1. VUISDK_V1.0 简介*](#1.-vuisdk-v1.0-简介)  
[*2. 项目使用条件*](#2.-项目使用条件)  
[*3. Demo*](#3.-demo)  
[*4. 快速开始*](#4.-快速开始)  
[*5. 参数介绍*](#5.-参数介绍)  
[*6. FAQ*](#6.-faq)  


## 1. VUISDK_V1.0 简介

**VUI SDK是roobo结合自身机器人和语音对话系统开发经验推出的一款包含基础语音能力和语音交互范式的软件开发包。VUI SDK连接roobo的语音语义服务平台，结合离线能力，给客户提供完整的语音系统开发能力支持。 
基于VUI SDK及背后的语音语义开发平台，开发者可以：**

- **1. 快速对接roobo AI平台，使用roobo全链路VUI服务。**  
- **2. 接入单项或多项语音交互基本能力。**  
- **3. 在已有的VUI交互方式上快速搭建业务逻辑。**  
- **4. 选择已有的技能或者自定义新技能。**  

## 2. 项目使用条件

android 设备

- **1. 联系商务申请ROSAI帐号并创建应用。**  
- **2. 提供应用的的AgentId给商务，获取SDK和Demo。**  

## 3. Demo
**Demo中提供了最常用的三种模式。**

- **模式1：唤醒+VAD+ASR+TTS**  
- **模式2：VAD+ASR+TTS**  
- **模式3：ASR+TTS**  

## 4. 快速开始

- **现在以模式二为例开始我们的Demo。  
目前SDK是以aar形式提供，所以需要使用Android Studio开发。把"ratn-release-xx-online.aar"拷贝到Libs文件夹下。在muoudle的build.gradle文件中添加。**

``` gradle
repositories {
    flatDir { dirs 'libs' }
}

dependencies {
    compile(name:'ratn-release-1.0-online',ext:'aar')
}
```
- **我们需要你创建一个带有按钮的页面，就像这样**  

![image.png](https://upload-images.jianshu.io/upload_images/11080649-b5a3d5be07ea6582.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **然后我们需要初始化我们的VUI**  
```Java
    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_mode_vad);
        initSDK();
        initView();
    }
``` 
- **initSDK()
初始化之前，需要先初始化参数。像这样**  
```Java
    private void initSDK(){
        VUIApi.InitParam.InitParamBuilder builder = new VUIApi.InitParam.InitParamBuilder();

        boolean isUseOnlineTTS = true;//设置TTS是否使用在线模式
        if (isUseOnlineTTS) {
            ttsType = RTTSPlayer.TTSType.TYPE_ONLINE;
        } else {
            ttsType = RTTSPlayer.TTSType.TYPE_OFFLINE;
        }

        builder.setLanguage("cmn-CHN")
                .setTTSType(ttsType)
                .setVUIType(VUIApi.VUIType.AUTO)
                .setAudioGenerator(new CustomAndroidAudioGenerator());

        mVUIApi = VUIApi.getInstance();
        mVUIApi.init(this, builder.build(), mInitListener);//绑定初始化监听器
    }
```
- **接下来**  
```Java
   private void initView() {
        mASRResultText = (TextView) findViewById(R.id.result_vad_mode);
        mStartBtn = (Button) findViewById(R.id.btn_start_vad_mode);
        mStartBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (!isRecording) {
                    isRecording = true;
                    mStartBtn.setText("点击结束识别");
                    //开始识别
                    AutoTypeController controller = (AutoTypeController) mVUIApi.startRecognize();
                    controller.manualWakeup();
                } else {
                    mStartBtn.setText("点击开始识别");
                    isRecording = false;
                    //结束识别
                    mVUIApi.stopRecognize();
                }
            }
        });
    }
```
- **重要的监听器  
InitListener  初始化回调**  
```Java 
    InitListener mInitListener = new InitListener() {

        @Override
        public void onSuccess() {
        }

        @Override
        public void onFail(RError message) {
        }
    };
```
- **RASRListener 识别结果回调**  
```Java
    RASRListener mASRListener = new RASRListener() {

        @Override
        public void onASRResult(ASRResult result) {
            String restText = "[识别结果]:" + result.getResultText();
        }

        @Override
        public void onFail(RError message) {
        }

        @Override
        public void onWakeUp(String json) {
        }

        @Override
        public void onEvent(EventType event) {
        }
    };
```
- **OnAIResponseListener  AI语义结果回调**  
```Java
    OnAIResponseListener mAIResponseListener = new OnAIResponseListener() {

        @Override
        public void onResult(String AI_JSON) {
        }

        @Override
        public void onFail(RError message) {
        }
    };
```
- **现在就可以运行你的App体验效果了。Have Fun！:blush:**  

## 5. 常见问题































































