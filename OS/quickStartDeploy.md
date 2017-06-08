## 示例工程是什么
示例工程是我们准备好的一套方便开发者快速集成的开发自身智能设备的一套软件开发包.

示例工程是  **一个开发包** 
示例工程是 **一个Android studio project**
示例工程 **可以语音交互整套流程**

后续会成为roobo开发包.

## 获取roobo开发包

点击**[roobo开发包下载](https://pan.baidu.com/s/1eSst5mU)  **获取开发包.
解压后会得到类似下图所示工程.不同时期下的版本可能后面的版本数字会有变化.
![](/assets/quickStartDeploy_1.png)

这是一个 android studio project .  用 android studio  open 的方式,不要使用 import .

![](/assets/quickStartDeploy_2.png)
![](/assets/quickStartDeploy_3.png)

## 项目资源简介

**interfaces/SceneSDK**  &emsp;         用于开发场景的sdk
**resource/apk/**         &emsp;        roobo提供服务的核心apk
**resource/data/sdcard/**   &emsp;      需要push到设备sdcard上的资源
**resource/scenesdk/**   &emsp;         用于场景开发的sdk内容,interfaces/SceneSDK中的内容来源于此. 包含 jar 于 so 文件,如果你使用其他的ide ,可以自行拷贝进行开发.
**scenes/**     &emsp;                 示例项目中内置的两个场景,后续会详细介绍这些场景的作用.新增的场景推荐都放在此目录下.
**scripts/**    &emsp;                  存放项目所需的脚本


## 部署工程到设备

#### 推荐更换签名
**roobotest.jks** 是开发包中内置的前面文件,将该签名文件更换为你的智能设备的系统签名文件.
**scripts/one_key_deploy.py**  打开该文件修改如下代码段为更新的签名文件信息.
![](/assets/quickStartDeploy_4.png)
更换签名不是必须,我们提供的默认签名依旧能帮你完成工程的部署.

#### 执行脚本部署
1.确保已经 [安装python](https://www.python.org/) 　
2.配置apk签名，打开**scripts/one_key_deploy.py** ，在下图所示处配置你的apk签名．
![](/assets/quickStartDeploy_5.png)
3.确保设备已经正确接入到pc机．adb shell 可用
4.执行脚本，python scripts/one_key_deploy.py 
有如下信息输出,代表部署成功.
![](/assets/quickStartDeploy_6.png)

#### 必要的检查
1.成功部署后，工程根部目录下产生build_outputs目录.确保build_outputs 目录下的所有apk 已经安装成功 
2.sn文件已经push到设备的sdcard 中.
3.设备的日期，时间为当前正确时间
4.音量已经打开
5.设备已经正确联网

#### 运行程序
如果你的设备有屏幕,有桌面那就找到名为 RooboShowMsg ,的app启动.
没有屏幕可以执行: adb shell am  start -n com.roobo.showmsg/.MainActivity
启动程序.
![](/assets/quickStartDeploy_7.png)
说出唤醒词 ,默认唤醒词为
**布丁布丁**
看到如图下图所示,并听到问候语,代表系统依旧唤醒可以开始输入语音指令.
![](/assets/quickStartDeploy_8.png)

语音输入
**今天天气**
![](/assets/quickStartDeploy_9.png)

至此示例程序已经部署运行成功. 现在所有的语音指令都会转到这个 "SHOW_MSG" 场景. 当然所有的数据都转发到这个场景处理肯定不是你所需要的.快速上手-自定义场景 , 快速上手-拆分场景数据. 这两章中会详细介绍.











