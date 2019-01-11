# 语音合成

## 提供的功能

* tts合成并播放，提供tts播放状态回调
* 停止正在播放的tts
* 获取当前是否在播放tts

## 示例

```java

//播放
int sessionId = TtsService.tts(cobtext, "播放语音", new TtsListener() {
            @Override
            public void onSpeakBegin() throws RemoteException {
                super.onSpeakBegin();
                //tts播放开始
            }

            @Override
            public void onCompleted() throws RemoteException {
                super.onCompleted();
                //tts播放结束
            }

            @Override
            public void onSpeakStopped() throws RemoteException {
                super.onSpeakStopped();
                //tts异常终止
            }

            @Override
            public void onSpeakFailed() throws RemoteException {
                super.onSpeakFailed();
                //tts失败
            }
        });

if (sessionId < 0) {
    //请求失败
}

//停止特定session id对应的tts
TtsService.stopTts(context, sessionId);

//停止所有tts
TtsService.stopTts(context);

//是否正在播放
TtsService.isSpeaking(context);

```
