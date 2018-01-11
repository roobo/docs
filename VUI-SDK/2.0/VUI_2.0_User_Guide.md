## 简介
---
VUI SDK是roobo结合自身机器人和语音对话系统开发经验推出的一款包含基础语音能力和语音交互范式的软件开发包。VUI SDK连接roobo的语音语义服务平台，结合离线能力，给客户提供完整的语音系统开发能力支持。
基于VUI SDK及背后的语音语义开发平台，开发者可以：
* 快速对接roobo AI平台，使用roobo全链路VUI服务
* 接入单项或多项语音交互基本能力
* 在已有的VUI交互方式上快速搭建业务逻辑
* 选择已有的技能或者自定义新技能
### 支持的VUI交互方式
| 交互方式| 说明 |
| ------------- |:-------------:|
| 机器人交互 |交互过程为：唤醒识别唤醒。在等待唤醒状态开发者可以手动唤醒。开始识别后，开发者需要根据业务逻辑选择超时休眠（回到等待唤醒状态）或者一次成功交互之后回到休眠状态。可参考布丁机器人及智能音箱等。 |
| 按钮式交互 | 交互过程为：开始识别识别结束识别。开发者需要调用特定的接口开始识别过程，并且调用结束时别接口结束整个识别过程。开始到结束之间的语音被当作是一个完整的句子送去识别。可参考现有的故事机产品以及其他靠按钮控制的语音交互产品。 |

### 支持的功能
1. 唤醒词识别、离线语音识别、在线语音识别。支持的语言参看附录的语言列表。
2. 离线、在线语音和成。支持的发言人/语言参考附录的对应的列表。
3. 语义理解。

## 申请帐号/获取SDK
---
1. 联系商务申请ROSAI帐号并创建应用。
2. 提供应用的的AgentId给商务，获取SDK和Demo。

## 集成SDK
---
### Step1 导入SDK
现在SDK是以aar形式提供，所以需要使用Android Studio开发。把"ratn-release-*-online.aar"拷贝到Libs文件夹下。在muoudle的build.gradle文件中添加
~~~
    repositories {
        flatDir { dirs 'libs' }
    }
    //*处需要替换成实际的版本号
    dependencies {
        compile(name:'ratn-release-*-online',ext:'aar')
    }
~~~

### step2 初始化SDK
~~~
VUIApi.getInstance().init(context, initParam,audioGenerator,initListener);
~~~
* audioGenerator

    音频生产者。SDK不关注音频是如何产生的，由开发者自己实现BaseAudioGenerator。Demo中已经实现了基于Android标准的 Recorder的CustomAndroidAudioGenerator,还有基于8009平台＋Roobo 6麦麦克风硬件的CustomSSEAudioGenerator。如果开发者是其他麦阵，需要自己去实现BaseAudioGenerator。

* initParam

    重要的几个参数

    | 参数| 说明 |必填　|
    | ------------- |:-------------:|:-------------:|
    | setLanguage() |设置ASR/TTS/AI的语言 |是|
    | setVUIType | 设置VUI交互方式 |是|
    | setTTSType | 设置TTS在线/离线模式 |是|
    | setTTSSpeaker | 如果TTS采用离线方式，这里设置是发音人。如果是采用离线方式，这是设置的是TTS语言 |否(默认"Li-Li")|
    | addOfflineFileName() | 设置离线语法文件，可用添加多个离线语法文件。Demo里有添加测试的离线语法文件，唤醒词是"智能管家" |否|
    | setUseSSE() | 是否使用SSE。采用Android标准的Recorder不需要使用SSE。如果是使用的多麦，需要使用SSE。|否(默认False)|
    | setSseMicCount() | 设置麦克风路数数量|如该使用SSE是必须的|
    | setSseRefCount() | 设置参考信号数量|如该使用SSE是必须的|
    | setBsdInSSE() | 设置SSE使用的Ssd文件|如该使用SSE是必须的|

## 语音识别
### **设置离线识别文件**
* 添加离线语法文件到assets/vocon下
* 调用接口添加语法文件
~~~
  BnfGrammar test_dynamic_offline_1 = new BnfGrammar("test_dynamic_offline_1");
  List<BnfGrammar> bnfGrammars = Arrays.asList(test_dynamic_offline_1);
      
     VUIApi.getInstance().getOfflineRecognizerController().loadGrammars(bnfGrammars, new LoadGrammarListener() {
            @Override
            public void onSuccess() {
                Toast.makeText(getApplicationContext(), "加载离线Grammar成功", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onFail(RError error) {
                Toast.makeText(getApplicationContext(), error.getFailDetail(), Toast.LENGTH_SHORT).show();
            }
        });

~~~

### **动态设置在线识别的语言(参考附录中的在线ASR语言范围)**
~~~
 VUIApi.getInstance().setCloudRecognizeLang(language);
~~~

---
### **设置Listener**
~~~
VUIApi.getInstance().setASRListener(new RASRListener() {
            @Override
            public void onASRResult(final ASRResult result) {
               //识别结果
            }

            @Override
            public void onFail(final RError message) {
               //识别失败
            }

            @Override
            public void onWakeUp(final String json) {
               //被唤醒。当时使用多麦的时候，还可用获取到唤醒角度
            }

            @Override
            public void onEvent(EventType event) {
                //语音识别过程中的事件，具体查看Api文档
            }
        });
~~~
### **开始识别**
~~~
 VUIApi.getInstance().startRecognize();
~~~
### **结束识别**
~~~
 VUIApi.getInstance().stopRecognize();
~~~
## 语义理解
---
### **文本语义理解**
文本语义是将自然语言的文本转换成语义结果．
~~~
 VUIApi.getInstance().setOnAIResponseListener(new OnAIResponseListener() {
            @Override
            public void onResult(final String json) {
               //语义成功结果
            }

            @Override
            public void onFail(final RError rError) {
　　　　　　　　 //语义失败
            }
        });
  VUIApi.getInstance().aiQuery(text);
~~~

### **语音语义理解**
语音语义理解是先把音频数据转为听写结果数据——自然语言的文本，再由服务器自动进行文本语义理解，相当于在文本语义前，先进行听写。不需要开发者去主动调用，ASR之后会主动请求语义并返回语义结果，开发只需要设置语义的回调．开发者可以登录ROAAI后台，去自定义自己的语义场景。

**语音语义设置Listener**
~~~
 VUIApi.getInstance().setOnAIResponseListener(new OnAIResponseListener() {
            @Override
            public void onResult(final String json) {
               //语义成功结果
            }

            @Override
            public void onFail(final RError rError) {
　　　　　　　　 //语义失败
            }
        });
~~~
### **语义理解上下文(现在只支持语音语义理解设置上下文)**
RooboAI后台的语义理解是支持上下文的，开发者可以设置上下文，就支持多轮对话。在AIResponseListener回调的中可以获取到outputContext。
~~~
VUIApi.getInstance().setAIContext(context);
~~~
## 语音合成
---
语音合成包括在线/离线两个方式，在SDK 初始化的时候设定的。
### **开始TTS**
~~~
VUIApi.getInstance().speak(text, new RTTSListener() {
            @Override
            public void onSpeakBegin() {
                //TTS开始
            }

            @Override
            public void onCompleted() {
　　　　　　　　　//TTS完成
            }

            @Override
            public void onError(int code) {
              //TTS出错
            }
        });
~~~
### **停止TTS**
~~~
 VUIApi.getInstance().stopSpeak();
~~~
### **动态修改speaker**
1. 修改在线发音人（参考附录中在线发音人范围）
~~~
 VUIApi.getInstance().setSpeaker("jpn-JPN");
~~~
2. 修改离线发音人(参考附录中离线发音人范围)
    * 在assets/vexpressive/config.xml中添加发音人的配置

    ~~~
    <speakers>
    <speaker name="Li-Li" language="cmn-CHN"/>
    <speaker name="Allison" language="eng-USA"/>
    </speakers>
    ~~~

    * 添加发音人的配置文件到assets/vexpressive中
    * 修改发音人
    ~~~
     VUIApi.getInstance().setSpeaker("Li-Li");
    ~~~
## 附录
---
1. 错误码

| 错误码 | 备注 |
| ------------- |:-------------:|
400 | BadRequest
401 | Unauthorized
500 | Internal
501 | NotSupported
503 | TooManyRequests
601 | ServiceUnAvailable
602 | ServiceUnknownFormat
603 | ServiceMismatch
604 | GetAsrServiceError
605 | SpeechRecognizeError
606 | SpeechRecognizeEmpty
607 | GetAiServiceError
608 | AiInternalError
609 | AiNotSupported
610 | GetTtsServiceError
611 | TtsServiceInternalError
10001 | 初始化language错误 
10002 | 重复初始化
10101 | 发送语音数据时 无法解析IP地址
10102 | 发送语音数据时 连接失败
10103 | 发送语音数据时 系统创建socket文件描述符失败
10104 | 发送语音数据时 执行send操作失败，通常是由于连接异常断开
10105 | 发送语音数据时 执行recv操作失败，通常是由于连接异常断开
10201 | 发送语音数据时 有错误的调用API的行为，如在一开始联网失败的情况下，还以ROOBOAUDIO_SAMPLE_LAST调用了RooboAudioWrite，目前这样的错误可以忽略。
21101 | 进行联网token校验时 无法解析IP地址
21102 | 进行联网token校验时 连接失败
21103 | 进行联网token校验时 系统创建socket文件描述符失败
21104 | 进行联网token校验时 执行send操作失败，通常是由于连接异常断开
21105 | 进行联网token校验时 执行recv操作失败，通常是由于连接异常断开
21201 | 进行联网token校验时 URL解析失败，URL在目前的封装下都是写在so内部，此错误不应该出现
21301 | 进行联网token校验时 服务端返回的http | body大小超出了8K的限制
21401 | 进行联网token校验时 在构造请求时，由于内存不足申请内存失败
21402 | 进行联网token校验时 在构造请求时创建请求线程失败，通常由于系统可用资源不足引起
22101 | 执行TTS文本转播放URL时 无法解析IP地址
22102 | 执行TTS文本转播放URL时 连接失败
22103 | 执行TTS文本转播放URL时 系统创建socket文件描述符失败
22104 | 执行TTS文本转播放URL时 执行send操作失败，通常是由于连接异常断开
22105 | 执行TTS文本转播放URL时 执行recv操作失败，通常是由于连接异常断开
22201 | 执行TTS文本转播放URL时 URL解析失败，URL在目前的封装下都是写在so内部，此错误不应该出现
22301 | 执行TTS文本转播放URL时 服务端返回的http | body大小超出了8K的限制
22401 | 执行TTS文本转播放URL时 在构造请求时，由于内存不足申请内存失败
22402 | 执行TTS文本转播放URL时 在构造请求时创建请求线程失败，通常由于系统可用资源不足引起
23101 | 在上传wifi列表获取位置时 无法解析IP地址
23102 | 在上传wifi列表获取位置时 连接失败
23103 | 在上传wifi列表获取位置时 系统创建socket文件描述符失败
23104 | 在上传wifi列表获取位置时 执行send操作失败，通常是由于连接异常断开
23105 | 在上传wifi列表获取位置时 执行recv操作失败，通常是由于连接异常断开
23201 | 在上传wifi列表获取位置时 URL解析失败，URL在目前的封装下都是写在so内部，此错误不应该出现
23301 | 在上传wifi列表获取位置时 服务端返回的http | body大小超出了8K的限制
23401 | 在上传wifi列表获取位置时 在构造请求时，由于内存不足申请内存失败
2. 语音识别支持的语音

| 语言码| 备注 |
| ------------- |:-------------:|
|cmn-CHN |中文 |
| en-US | 英文 |
3. 离线TTS支持的发音人

| 发音人| 备注 |
| ------------- |:-------------:|
| Li-Li |中文 |
| Allison | 英文 |
4. 在线TTS支持的语言