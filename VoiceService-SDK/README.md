VoiceService-SDK 开发指南v1.0.0
==

### 目录

[1.概述](#概述)

[2.使用说明](#使用说明)
* [2.1 准备](#准备)
* [2.2 主要流程](#主要流程)
* [2.3 使用步骤](#使用步骤)

[3.错误码对应表](#错误码对应表)

### 概述
VoiceService-SDK运行在Android平台的SDK，旨在为用户提供在线的语音听写、语义分析及语音合成的能力，目前支持语言中文和英文。

### 使用说明
#### 准备
 1. 账号申请，账号通常包括agentID，agentToken，如果是Roobo分配的设备ID，则需要同时拿到clientID。
 2. SDK及demo获取，目前SDK是以aar的形式提供，IDE需要用AndroidStudio。
#### 主要流程
SDK主要流程如下：

```flow
st=>start: Start
e=>end
cond=>condition: init with 
UserInfo 
sucessed ?
ops=>operation: start and wait asr 
or ai or tts result
ope=>operation: get result
opr=>operation: quit and release engin


st->cond->ops->ope->opr->e
cond(yes)->ops
cond(no)->cond
```

#### 使用步骤
1. 配置编译环境，将SDK的aar文件放入业务Module的libs文件夹下，并且配置编译选项
    
    repositories {
        flatDir { dirs 'libs' }
    }
    dependencies {
        compile(name:'voicesdk-release-1.0.2-test',ext:'aar')
    }

2. 初始化
    
    Authentification authentification = new Authentification();
	UserInfo userInfo = createUserInfo();
    authentification.login(userInfo, new LoginResultListener() {
            @Override
            public void onSucess() {
            }
            @Override
            public void onFail(final RError message) {
            }
    });
    private UserInfo createUserInfo() {
        UserInfo userInfo = new UserInfo(this);
        /**
         * UserInfo.DeviceIDType.TYPE_ROOBO如果是提前分配好了ClientID，请选择这个类型。
         * 否则选择UserInfo.DeviceIDType.TYPE_USER_DEFINE
         */
        userInfo.setDeviceIDType(UserInfo.DeviceIDType.TYPE_USER_DEFINE);
        //        userInfo.setDeviceIDType(UserInfo.DeviceIDType.TYPE_ROOBO);
        /**
         * @see UserInfo.DeviceIDType
         */
        userInfo.setDeviceID("yourDeviceID");
        /**
         * 请妥善保管您的账号信息
         */
        userInfo.setAgentID("yourAgentID");
        userInfo.setAgentToken("yourAgentToken");
        userInfo.setProduction("yourProduction");
        return userInfo;
    }

3. 在线识别、语义
初始化成功后可以使用在线识别和语义，用户需要将Recorder的数据通过SDK的write接口送给SDK，例如：
    
    AudioRecord record = new AudioRecord(MediaRecorder.AudioSource.MIC, 16000,
        AudioFormat.CHANNEL_IN_MONO, AudioFormat.ENCODING_PCM_16BIT, bufferSize);
    byte[] buffer = new byte[bufferSize];
    record.startRecording();
    while (mIsRecoging) {
        int len = record.read(buffer, 0, bufferSize);
        if (len > 0) {
        synchronized (rooboLock) {
            if (mRooboRecognizer != null) {
                mRooboRecognizer.writeVoiceData(buffer, len);
            }
        }
    }

4. 在线TTS
初始化成功后可以使用在线TTS，只需要将需要转换为TTS的文本数据送给SDK的TTS接口即可返回对应的TTS数据url。

### 错误码对应表

error code | error des
------------ | ---------------------------------------------------------------
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

