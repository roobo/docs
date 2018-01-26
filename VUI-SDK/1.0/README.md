###  目录
  [1.简介](#1)

  [2.集成SDK](#2)
  * [2.1　导入SDK](#2.1)
  * [2.2　SDK接口使用](#2.2)


  [3.错误对应码](#3)

  [4.在线识别支持的语言列表](#4)
  
  [5.离线识别支持的语言列表](#5)
  
  [6.在线发音人列表](#6)
  
  [7.离线发音人列表](#7)
  
  [8.在线AI支持的语言列表](#8)
  
  
  
  
<h3 id="1">1.简介 </h3>

VUI SDK是roobo结合自身机器人和语音对话系统开发经验推出的一款包含基础语音能力和语音交互范式的软件开发包。VUI SDK连接roobo的语音语义服务平台，结合离线能力，给客户提供完整的语音系统开发能力支持。
基于VUI SDK及背后的语音语义开发平台，开发者可以：
* 快速对接roobo AI平台，使用roobo全链路VUI服务
* 接入单项或多项语音交互基本能力
* 在已有的VUI交互方式上快速搭建业务逻辑
* 选择已有的技能或者自定义新技能

**VUI交互方式**

| 交互方式 | 说明 |
| ------------- |:-------------:|
| 机器人交互 |交互过程为：唤醒识别唤醒。在等待唤醒状态开发者可以手动唤醒。开始识别后，开发者需要根据业务逻辑选择超时休眠（回到等待唤醒状态）或者一次成功交互之后回到休眠状态。可参考布丁机器人及智能音箱等。 |
| 按钮式交互 | 交互过程为：开始识别识别结束识别。开发者需要调用特定的接口开始识别过程，并且调用结束时别接口结束整个识别过程。开始到结束之间的语音被当作是一个完整的句子送去识别。可参考现有的故事机产品以及其他靠按钮控制的语音交互产品。 |

**语言**
目前支持语言请参见支持的语言。

**可选的功能**
离线唤醒、打断，离线短语识别，在线语句识别，在线语义，离线语音合成，在线语音合成。

**申请帐号/获取SDK**
1. 联系商务申请ROSAI帐号并创建应用。
2. 提供应用的的AgentId给商务，获取SDK和Demo。

**接口文档**
[地址](http://htmlpreview.github.com/?https://github.com/roobo/docs/blob/master/VUI-SDK/1.0/javaDoc/index.html)

<h3 id="2">2.集成SDK</h3>

<h4 id="2.1">2.1 导入SDK</h4>

现在SDK是以aar形式提供，所以需要使用Android Studio开发。把"ratn-release-*-online.aar"拷贝到Libs文件夹下。在muoudle的build.gradle文件中添加

```
    repositories {
        flatDir { dirs 'libs' }
    }
    dependencies {
        compile(name:'ratn-release-1.0-online',ext:'aar')
    }

```
***DEMO下载***
[地址](https://github.com/roobo/docs/blob/master/VUI-SDK/1.0/VUISDKDemo.zip)

<h4 id="2.2">2.2 SDK接口使用</h5>

#### 初始化SDK
~~~
VUIApi.getInstance().init(context, initParam,initListener);
~~~

* initParam

    重要的几个参数

    | 参数| 说明 |必填　|
    | ------------- |:-------------:|:-------------:|
    | setLanguage() |设置ASR/TTS/AI的语言 |是|
    | setVUIType | 设置VUI交互方式 |是|
    | setTTSType | 设置TTS在线/离线模式 |是|
    | setTTSSpeaker | 如果TTS采用离线方式，这里设置是发音人。如果是采用在线方式，这是设置的是TTS语言 |否(默认"Li-Li")|
    | setAudioGenerator() | 设置语音识别的音源 |是|
    | setUserInfo() | 通常不会调用此方法，仅用于给客户预分配SN和PublicKey的场景 | 否（默认是通过android默认的serialno来确认设备的唯一性，所以必须保证serialno的唯一性）|
    
    注意：设置SN请调用UserInfo.setDeviceID(),设置PublicKey请调用UserInfo.setPublicKey（）。

#### 语音识别
* ##### **设置离线识别文件**
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

* ##### **动态设置在线识别的语言(参考附录中的在线ASR语言范围)**
    ~~~
    VUIApi.getInstance().setCloudRecognizeLang(language);
    ~~~


* ##### **设置Listener**
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
* ##### **开始识别**
    ~~~
    VUIApi.getInstance().startRecognize();
    ~~~
* ##### **结束识别**
    ~~~
    VUIApi.getInstance().stopRecognize();
    ~~~
#### 语义理解
---
* ##### **文本语义理解**
    文本语义是将自然语言的文本转换成语义结果。注意：文本语义理解暂不支持设置上下文和地理位置。
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

* ##### **语音语义理解**
    语音语义理解是先把音频数据转为听写结果数据——自然语言的文本，再由服务器自动进行文本语义理解，相当于在文本语义前，先进行听写。不需要开发者去主动调用，ASR之后会主动请求语义并返回语义结果，开发只需要设置语义的回调．开发者可以登录ROAAI后台，去自定义自己的语义场景。 

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
* ##### **语义理解上下文(现在只支持语音语义理解设置上下文)**
    RooboAI后台的语义理解是支持上下文的，开发者可以设置上下文，就支持多轮对话。在AIResponseListener回调的中可以获取到outputContext。
    ~~~
    VUIApi.getInstance().setAIContext(context);
    ~~~
* ##### **语义理解地理位置上报接口**
    在地理位置相关的请求，我们提供了上报地理位置的接口来解决此类问题。例如：问设备当地的天气。
    ~~~
    VUIApi.getInstance().reportLocationInfo(List<ScanResult> scanResultList);
    VUIApi.getInstance().reportLocationInfo(String latitude, String longitude, String country, String province, String city, String detail);
    ~~~

#### 语音合成
---
语音合成包括在线/离线两个方式，在SDK 初始化的时候设定的。
* ##### **开始TTS**
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
* ##### **停止TTS**
    ~~~
    VUIApi.getInstance().stopSpeak();
    ~~~
* ##### **动态修改speaker**
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

<h3 id="3">3.错误对应码</h3>

| 错误码 | 备注 |
| ------------- |:-------------:|
100 | please check user info
101 | session begin error
102 | token invalid
103 | server result error
104 | can not link to server,please check net work
200 | not have tts content
201 | vad init error
202 | speech timeout
203 | wait server response result time out
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
901 | no network
900 | unkown error,please check the exception info in log
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

<h3 id="4">4.在线识别支持的语言列表</h3>

| 语言| 语言对应的code |
| ------------- |:-------------:|
|	Arabic (Egypt)	|	ara-EGY	|
|	Arabic (Saudi Arabia)	|	ara-SAU	|
|	Arabic (International)	|	ara-XWW	|
|	Bahasa (Indonesia)	|	ind-IDN	|
|	Cantonese (Simplified)	|	yue-CHN	|
|	Catalan	|	cat-ESP	|
|	Croatian 	|	hrv-HRV	|
|	Czech	|	ces-CZE	|
|	Danish	|	dan-DNK	|
|	Dutch	|	nld-NLD	|
|	English (Australia)*	|	eng-AUS	|
|	English (GB)*	|	eng-GBR	|
|	English (US)*	|	eng-USA	|
|	English (India) 	|	eng-IND	|
|	Finnish	|	fin-FIN	|
|	French (Canada)	|	fra-CAN	|
|	French (France)*	|	fra-FRA	|
|	German*	|	deu-DEU	|
|	Greek	|	ell-GRC	|
|	Hebrew	|	heb-ISR	|
|	Hindi	|	hin-IND	|
|	Hungarian	|	hun-HUN	|
|	Italian	|	ita-ITA	|
|	Japanese	|	jpn-JPN	|
|	Korean	|	kor-KOR	|
|	Malay	|	zlm-MYS	|
|	Mandarin (China/Simplified)	|	cmn-CHN	|
|	Mandarin (Taiwan/Traditional)	|	cmn-TWN	|
|	Norwegian	|	nor-NOR	|
|	Polish	|	pol-POL	|
|	Portuguese (Brazil)	|	por-BRA	|
|	Portuguese (Portugal)	|	por-PRT	|
|	Romanian	|	ron-ROU	|
|	Russian	|	rus-RUS	|
|	Slovak	|	slk-SVK	|
|	Spanish (Spain)	|	spa-ESP	|
|	Spanish (LatAm)	|	spa-XLA	|
|	Swedish	|	swe-SWE	|
|	Thai	|	tha-THA	|
|	Turkish	|	tur-TUR	|
|	Ukrainian	|	ukr-UKR	|
|	Vietnamese	|	vie-VNM	|

<h3 id="5">5.离线识别支持的语言列表</h3>

| 语言| 语言对应的code |
| ------------- |:-------------:|
|	US English	|	eng-USA	|
|	Spanish(LatAM)	|	spa-XLA	|
|	Russian	|	rus-RUS	|
|	Spanish(Spain)	|	spa-ESP	|
|	French for France	|	fra-FRA	|
|	German	|	deu-DEU	|
|	Danish	|	dan-DNK	|
|	Italian	|	ita-ITA	|
|	Dutch	|	nld-NLD	|
|	Mandarin	|	cmn-CHN	|
|	Cantonese Traditional	|	yue-CHN	|
|	Korean	|	kor-KOR	|
|	Japanese	|	jpn-JPN	|
|	arabic	|	ara-XWW	|
|	Polish	|	pol-POL	|
|	turkish	|	tur-TUR	|

<h3 id="6">6.在线发音人列表</h3>

| 语言| 语言对应的code |
| ------------- |:-------------:|
|	Arabic (Egypt)	|	ara-EGY	|
|	Arabic (Saudi Arabia)	|	ara-SAU	|
|	Arabic (International)	|	ara-XWW	|
|	Bahasa (Indonesia)	|	ind-IDN	|
|	Cantonese (Simplified)	|	yue-CHN	|
|	Catalan	|	cat-ESP	|
|	Croatian 	|	hrv-HRV	|
|	Czech	|	ces-CZE	|
|	Danish	|	dan-DNK	|
|	Dutch	|	nld-NLD	|
|	English (Australia)*	|	eng-AUS	|
|	English (GB)*	|	eng-GBR	|
|	English (US)*	|	eng-USA	|
|	English (India) 	|	eng-IND	|
|	Finnish	|	fin-FIN	|
|	French (Canada)	|	fra-CAN	|
|	French (France)*	|	fra-FRA	|
|	German*	|	deu-DEU	|
|	Greek	|	ell-GRC	|
|	Hebrew	|	heb-ISR	|
|	Hindi	|	hin-IND	|
|	Hungarian	|	hun-HUN	|
|	Italian	|	ita-ITA	|
|	Japanese	|	jpn-JPN	|
|	Korean	|	kor-KOR	|
|	Malay	|	zlm-MYS	|
|	Mandarin (China/Simplified)	|	cmn-CHN	|
|	Mandarin (Taiwan/Traditional)	|	cmn-TWN	|
|	Norwegian	|	nor-NOR	|
|	Polish	|	pol-POL	|
|	Portuguese (Brazil)	|	por-BRA	|
|	Portuguese (Portugal)	|	por-PRT	|
|	Romanian	|	ron-ROU	|
|	Russian	|	rus-RUS	|
|	Slovak	|	slk-SVK	|
|	Spanish (Spain)	|	spa-ESP	|
|	Spanish (LatAm)	|	spa-XLA	|
|	Swedish	|	swe-SWE	|
|	Thai	|	tha-THA	|
|	Turkish	|	tur-TUR	|
|	Ukrainian	|	ukr-UKR	|
|	Vietnamese	|	vie-VNM	|


<h3 id="7">7.离线发音人列表</h3>

| 语言 | 语言对应的code | 发音人 |
| ------------- |:-------------|:-------------:|
|	Arabic	|	ara-XWW	|	Laila	|
|	Bahasa (Indonesia)	|	ind-IDN	|	Damayanti	|
|	Basque	|	baq-ESP	|	Miren	|
|	Cantonese	|	yue-CHN	|	Sin-Ji	|
|	Catalan	|	cat-ESP	|	Jordi	|
|	Czech	|	ces-CZE	|	Iveta	|
|	Danish	|	dan-DNK	|	Magnus	|
|	Dutch	|	nld-NLD	|	Claire	|
|	Dutch (Belgium)	|	nld-BEL	|	Ellen	|
|	English (Australia)	|	eng-AUS	|	Karen	|
|	English (GB)	|	eng-GBR	|	Daniel	|
|	English (India)	|	eng-IND	|	Veena	|
|	English (Ireland)	|	eng-IRL	|	Moira	|
|	English (Scotland)	|	eng-SCT	|	Fiona	|
|	English (South Africa)	|	eng-ZAF	|	Tessa	|
|	English (US)	|	eng-USA	|	Allison	|
|	Finnish	|	fin-FIN	|	Satu	|
|	French	|	fra-FRA	|	Audrey-ML	|
|	French (Canada)	|	fra-CAN	|	Amelie	|
|	Galician	|	glg-ESP	|	Carmela	|
|	German	|	deu-DEU	|	Markus	|
|	Greek	|	ell-GRC	|	Melina	|
|	Hebrew	|	heb-ISR	|	Carmit	|
|	Hindi	|	hin-IND	|	Lekha	|
|	Hungarian	|	hun-HUN	|	Mariska	|
|	Italian	|	ita-ITA	|	Alice-ML	|
|	Japanese	|	jpn-JPN	|	Kyoko	|
|	Korean	|	kor-KOR	|	Sora	|
|	Mandarin (China)	|	cmn-CHN	|	Li-Li	|
|	Mandarin (Taiwan)	|	cmn-TWN	|	Mei-Jia	|
|	Norwegian	|	nor-NOR	|	Nora	|
|	Polish	|	pol-POL	|	Ewa	|
|	Portuguese (Brazil)	|	por-BRA	|	Luciana	|
|	Romanian	|	ron-ROU	|	Ioana	|
|	Russian	|	rus-RUS	|	Katya	|
|	Slovak	|	slk-SVK	|	Laura	|
|	Spanish (Castilian)	|	spa-ESP	|	Jorge	|
|	Spanish (Columbia)	|	spa-COL	|	Soledad	|
|	Spanish (Mexico)	|	spa-MEX	|	Angelica	|
|	Swedish	|	swe-SWE	|	Alva	|
|	Thai	|	tha-THA	|	Kanya	|
|	Turkish	|	tur-TUR	|	Cem	|
|	Valencian	|	spa-ESP	|	Empar	|



<h3 id="8">8.在线AI支持的语言列表</h3>

| 语言码| 备注 |
| ------------- |:-------------:|
|	US English	|	eng-USA	|
|	Mandarin	|	cmn-CHN	|



