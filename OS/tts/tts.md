# 语音合成

## 提供的功能

* tts合成并播放，提供tts播放状态回调
* 停止正在播放的tts
* 获取当前是否在播放tts

## 示例

```java

//播放
TtsService.playText(cobtext, "播放语音", new TtsListener() {
            @Override
            public void onSpeakBegin() throws RemoteException {
                super.onSpeakBegin();
            }

            @Override
            public void onSpeakPaused() throws RemoteException {
                super.onSpeakPaused();
            }

            @Override
            public void onSpeakResumed() throws RemoteException {
                super.onSpeakResumed();
            }

            @Override
            public void onCompleted() throws RemoteException {
                super.onCompleted();
            }
        });

//停止
TtsService.stopTts(context);

//是否正在播放
TtsService.isSpeaking(context);

```
