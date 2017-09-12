## 示例工程是什么
示例工程是我们准备好的一套方便开发者快速集成的开发自身智能设备的一套软件开发包.

示例工程是  **一个开发包** 
示例工程是 **一个Android studio project**
示例工程 **可以语音交互整套流程**

后续会成为roobo开发包.

## 获取roobo开发包

点击**[roobo开发包下载](https://pan.baidu.com/s/1bXCcTS)  **获取开发包.
解压后会得到类似下图所示工程.不同时期下的版本可能后面的版本数字会有变化.
![](/智能手表/assets/quickStartDeploy_1.png)
若您希望的是快速看到效果，可以直接转到　**执行脚本部署 **

获取到的开发包是一个 android studio project .  用 android studio  open 的方式,
切记不要使用 import .
![](/智能手表/assets/quickStartDeploy_2.png)
![](/智能手表/assets/quickStartDeploy_3.png)

## 项目资源简介

**interfaces/SceneSDK**  
&emsp;     用于开发场景的sdk
**resource/apks/**         
roobo提供服务的核心apk:

&emsp; PlatformService-release-roobo_dot-baochenhe-24-1.1.1918-online.apk
&emsp;另外的apk 属于教学的场景apk,开发包中包含源码。

**resource/data/sdcard/**   &emsp;      需要push到设备sdcard上的资源，

**resource/scenesdk/**   &emsp;         用于场景开发的sdk内容,interfaces/SceneSDK中的内容来源于此. 包含 jar 于 so 文件,如果你使用其他的ide ,可以自行拷贝进行开发.

**scenes/**     &emsp;                 示例项目中内置的两个场景,后续会详细介绍这些场景的作用.新增的场景推荐都放在此目录下.

**scripts/**    &emsp;                  存放项目所需的脚本

**deploy.sh 与　deploy.bat** &emsp;   分别为linux 与 windows 系统的部署脚本。


## 部署工程到设备

#### 执行脚本部署
1.确保设备已经正确接入到pc机．adb shell 可用
2.根据自己的系统选择不同的　deploy 脚本。　
* linux ： sh deploy.sh
* windows: 双击deploy.bat
* 脚本所做的工作是：将resource/data/sdcard/　目录下的资源　push 到设备的sdcard.然后安装resource/apks/目录下的apk,最后重启设备。

#### 必要的检查
1.成功部署后，确保resource/apks/ 目录下的所有apk 已经安装成功 
2.resource/scenesdk/ 目录下的文件已经push到设备的sdcard 中.
3.设备的日期，时间为当前正确时间
4.音量已经打开
5.设备已经正确联网
6.Android6.0 以上的设备需要检查PlatformService（roobo核心服务），麦克风，存储，启动app等权限是否开启。

#### 运行程序
如果你的设备有屏幕,有桌面那就找到名为 RooboDemo ,的app启动.
启动程序.
![](/智能手表/assets/quickStartDeploy_4.png)

语音输入
**今天天气**
![](/智能手表/assets/quickStartDeploy_5.png)

至此示例程序已经部署运行成功. 现在所有的语音指令都会转到这个 "SHOW_MSG" 场景. 当然所有的数据都转发到这个场景处理肯定不是你所需要的.快速上手-自定义场景 , 快速上手-拆分场景数据. 这两章中会详细介绍.











