## 1 集成准备

### 1.1 [StoryMachineDemo下载](http://pan.baidu.com/s/1eROboWE)
### 1.2 resource内容介绍：(StoryMachineDemo的resource文件夹)
    - lib: 场景开发的jar及Jni
    - data:规则配置文件和sn
    - PlatformService*.apk PlatformService Apk
    - deploy.py 部署脚本

## 2 product 配置
### 2.1 到ROS.AI 服务器申请新的Product
### 2.2 修改product name
修改resource/data/sdcard/ros/configure/production_config.xml 中的 "device.production" 的value
### 2.3 修改sn
修改resource/data/sdcard/sn 中的数据

## 3 场景开发
### 3.1 场景开发请参考 Roobo OS [开发指南](https://github.com/roobo/docs/blob/master/OS/SUMMARY.md)

## 4 部署

### 4.1 生成output
```java
./gradlew clean output
````

### 4.2 到output 文件夹中执行部署脚本
```java
 python deploy.py  debug/release old/new
````

## 5 验证是否成功
- 1.启动platformService.apk
- 2.对着手机说"罗赛"
- 3.手机能够回答你"在","我在"
- 4.接着问"今天天气怎么样"
- 5.如果手机能正常回答你的问题就证明PlatformService运行正常

## 6 注意事项
- 1.当部署在手机或者第三方平台上时候，需要注意权限