###  目录
  [1.概述](#1)

  [2.使用说明](#2)
  * [2.1　准备](#2.1)
  * [2.2　API初始化](#2.2)
  * [2.3　方法及参数解析](#2.3)


  [3.错误对应码](#3)

  [4.支持的语音列表](#4)
  
  [5.发音人列表](#5)
  
  
  
  
<h3 id="1">1.概述 </h3>

VUI-SDK是运行在Android平台，旨在为用户提供完整的语音交互功能。其中内置两个标准的交互方案，1.标准的机器人交互方案，可全部通过语音控制整个交互流程。可参考市场上售卖的机器人及各种音响产品等。2.类似故事机的按钮式交互方案，主要是通过按钮控制整个交互流程。

**语言**目前支持语言请参见支持的语言。

**可选的功能**离线唤醒、打断，离线短语识别，在线语句识别，在线语义，离线语音合成，在线语音合成。

**demo获取**

##### [demo下载](http://)

**接口文档**
[地址](http://htmlpreview.github.com/?https://github.com/roobo/docs/blob/master/VUI-SDK/javadoc/index.html)


<h3 id="2">2.使用说明</h3>

<h4 id="2.1">准备</h4>

1.账号申请、SDK及demo获取，目前SDK是以aar的形式提供，IDE需要用AndroidStudio。
2.对应语种唤醒词，离线短语的语法文件。
3.配置编译环境，将SDK的aar文件放入业务Module的libs文件夹下，并且配置编译选项

```
    repositories {
        flatDir { dirs 'libs' }
    }
    dependencies {
        compile(name:'ratn-release-1.0-online',ext:'aar')
    }

```

<h5 id="2.2">2.2方法及参数解析</h5>

###### 核心接口类：
VUIApi。

###### 核心方法：

初始化SDK：
**init(Context context, InitParam initParam, InitListener initListener)**

开始识别：
**startRecognize()**

结束识别：
**stopRecognize()**

语义结果监听：
**setOnAIResponseListener(OnAIResponseListener listener)**

识别结果及状态变化监听：
**setASRListener(AsrEventListener asrEventListener)**

语音合成、播放：
**speak(String text)**

停止语音合成、播放：
**stopSpeak()**

语音播放过程监听：
**setTTSListener(RTTSListener listener)**

<h3 id="3">错误对应码</h3>

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

<h3 id="5">支持的语言列表</h3>

| 语言码| 备注 |
| ------------- |:-------------:|
|cmn-CHN |中文 |
| en-US | 英文 |

<h3 id="4">发音人</h3>

| 语言码| 备注 |
| ------------- |:-------------:|
| Li-Li |中文 |
| Allison | 英文 |



