###  目录
  [1.概述](#1)

  [2.使用说明](#2)
  * [2.1　准备](#2.1)
  * [2.2　API初始化](#2.2)
  * [2.3　方法及参数解析](#2.3)


  [3.错误对应码](#3)

  [4.支持的语音列表](#4)
  
  
  
  
<h3 id="1">1.概述 </h3>

RATN-SDK是运行在Android平台，旨在为用户提供在线语音听写、唤醒及离线语音合成的能力。
**麦克风:** 支持android 标准的,与roobo公司的环形麦克风阵列record。
**语言：**目前支持语言请参见支持的语言。

##### [sdk下载](http://)


<h3 id="2">2.使用说明</h3>

<h4 id="2.1">准备</h4>

1.账号申请，账号通常包括appID，publicKey，账号注意妥善保管。
2.SDK及demo获取，目前SDK是以aar的形式提供，IDE需要用AndroidStudio。
3.对应语种的资源，每个语言包含对应的离线识别、TTS合成的模型文件。
4.配置编译环境，将SDK的aar文件放入业务Module的libs文件夹下，并且配置编译选项

```
    repositories {
        flatDir { dirs 'libs' }
    }
    dependencies {
        compile(name:'rat-release-1.0.2-online',ext:'aar')
    }

```

<h5 id="2.2">2.2API初始化</h5>

本sdk支持三种初始化方式

**initWakeupSingleRecognizeApi**

该模式下的api,每次发布指令前，需要先语音输入唤醒词，当设备接收到唤醒词后，可以输入具体的命令如：**今天天气怎么样** 。命令识别成功后，会重新回到需要说唤醒的状态。该状态我们定义为**SLEEP**状态。

**initSustainedWakeupAndCloudRecognizeApi**

该模式下的api,首次发布命令前需要先语音输入唤醒词，当设备接收到唤醒词后，可以输入具体的命令，如：**今天天气怎么样**，也可以再次输入唤醒词，命令识别成功后，不会进入**SLEEP**状态，而是会一直处于识别状态，该状态我们定义为**ACTIVE**。

**initManualVADRecognizeApi**
该模式下的api不包含**VAD**,而其他初始化得到的api，都配备有智能VAD。该api由用户手动控制vad的开始与结束。比较试用于智能手表。有一个按钮，按下开始输入命令，抬起则结束输入，开始识别命令。


<h5 id="2.3">2.3方法及参数解析</h5>

###### 参数解析

| 类型 | 参数 | 备注 |
| ------------- |:-------------:| -----:|
| Context | context | 程序的context |
| String | language | api识别对应的语言 |
| MicModel | micModel | 麦克类型：<br/>ANDROID_STANDARD　标准<br/> MIC_ARRAY_R16 环形麦克风阵列|
| String | wakeupGrammarFile |唤醒词资源文件 |
| List<String> | word | 唤醒词资源文件中包含的唤醒词列表 |
| UserInfo | userInfo | 用户账号信息 |
| InitListener | initListener | 初始化Callback |


###### 核心方法解析：

开始识别：
**startRecognizer()**

结束识别：
**stopRecognizer()**

识别结果监听：
**setRecognizerListener(RecognizerResultListener listener)**
```
public interface RecognizerResultListener {
    /**　唤醒 **/
    void onWakeup(String json);

    /** 语义识别结果**/
    void onCloudResult(String json);
}
```
识别过程中的状态变化：
**setAsrEventListener(AsrEventListener asrEventListener)**


<h3 id="3">错误对应码</h3>

| 错误码 | 备注 |
| ------------- |:-------------:|
| 10001 | 初始化language错误 |
| 10002 | 重复初始化 |


<h3 id="4">支持的语言列表</h3>

| 语言码| 备注 |
| ------------- |:-------------:|
|cmn-CHN |中文 |
| en-US | 英文 |



