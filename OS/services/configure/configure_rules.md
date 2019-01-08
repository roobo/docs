## 配置中心规则
配置中心是存储状态和配置信息的地方。通过数据库将各类信息保存下来。配置中心的规则用于数据库定义和数据表的预置数据定义以及rml文件定义。

### 数据库定义
数据表的定义放在ConfigureLib模块的src/main/res/xml下的roobo_os_database.xml中。

roobo_os_database.xml实例如下：
```xml
<databases version="1">
    <table name="DeveloperConfig" file="developer_config" system="false" clear="false">
        <col name="key" type="varchar"/>
        <col name="value" type="varchar"/>
        <col name="type" type="varchar"/>
    </table>
    <table name="GlobalConfig" file="roobo_os_global_config|production_config"
      system="true" clear="true">
        <col name="key" type="varchar"/>
        <col name="value" type="varchar"/>
        <col name="type" type="varchar"/>
    </table>

    <!-- ... -->
</databases>
```

### 版本号
databases下的version属性，用于标记当前整套预置数据定义文件的版本


### table标签
每个table标签定义了数据库中的一个表，标签下的属性如下：

name ：表名

file ：预置数据定义文件，为表提供初始数据，可来自多个文件，用|分开，有以下三类配置，存放与不同的路径
```
系统通用配置（ConfigureLib模块下的src/main/res/xml）
文件名一般以roobo_os_开头，不可修改

产品相关的配置（根目录Configure/production/<当前的production>/resource/data/res/xml/）
文件名一般以production_开头，不同产品具有差异性第三方开发者不可修改，
（该目录被Configure模块引用，根据预编译脚本切换，会在打包时放入Configure）。

可供开发者修改的配置（设备sdcard/ros/configure/）
文件名一般以developer_开头，开发者可修改
（也可以开发阶段放在sd卡下，在上线前挪入production中随Configure模块一起编入apk）
```
system ：声明是否为系统专用的表，如果为true，加载预置数据定义文件时会跳过设备sdcard/ros/configure/目录

clear ：声明该表是否持久化，如果为true，该表的数据会在关机时丢失

### 子标签col
声明表中每一列的属性

name：表中列的名字

type：该字段对应的数据类型

### 预置数据定义文件

数据库初始化时导入的原始数据

例如GlobalConfig表的预置数据定义文件为roobo_os_global_config.xml和production_config.xml

拿roobo_os_global_config.xml举例来说，内部定义如下：

```xml
<config>
  <item key="updater.production" type="string" value="storybox" />
  <!-- ... -->
</config>
```
数据定义中的每一行都应该与roobo_os_database.xml中相应表定义的字段匹配。不能匹配的条目将被忽略。

每个字段的值都以字符串表示，实际生成数据库的时候会根据字段类型做转化。

### 表数据初始化加载流程
每次Configure模块启动时都会尝试从预置数据定义文件中获取最新的配置

加载数据的流程大体如下：

```
1.从roobo_os_database.xml中查询表的预置数据定义文件名列表，从左至右逐个遍历

2.每当遍历到一个文件名，首先会从Configure模块src/main/res/xml/下查找是否有同名的xml文件，
如果有从中提取需要更新的数据，等待写入数据库

3.如果该表不是系统专用（system属性为false），还会尝试从设备的sdcard/ros/configure/下查找是否有同名的xml文件，
提取需要更新的数据，等待写入数据库，如果是系统专用（system属性为true）则跳过此目录

4.如果该表不需要持久化（clear属性为true），则会创建内存数据库
如果不需要持久化（clear属性为false），则会创建本地数据库

5.将提取的数据写入数据库

注意：
提取需要更新数据的逻辑：
对于res/xml下的配置：
如果该表的clear属性为true，则会全量加入需要更新的列表
如果数据库version有更新，则会全量加入需要更新的列表

对于sdcard下的配置：
如果当前系统时间大于某一列之前修改的时间，则会将这一列加入需要更新的列表

```

### 运行期获取和修改配置
通过ConfigureInterface模块下Configure类的getConfig方法来获取当前生效的key对应的value

优先从GlobalConfig表中查询，如果没有则尝试从DeveloperConfig中查询

```
Object getConfig(Context context, String key)
```
通过ConfigureInterface模块下Configure类的setConfig方法来修改当前生效的key的value

（需要注意的是，如果定义该key的表clear属性为true，此次修改会在重启后会失效）
```
void setConfig(Context context, String key, Object value)
```
### rml文件
和预置数据定义文件类似，rml也分为三类
```
系统通用rml文件（ConfigureLib模块下的src/main/res/xml）
不可修改

产品相关的rml文件（根目录Configure/production/<当前的production>/resource/data/res/xml/）
文件名以production_rml_开头，不同产品具有差异性第三方开发者不可修改，
（该目录被Configure模块引用，根据预编译脚本切换，会在打包时放入Configure）。

可供开发者修改的rml文件（设备sdcard/ros/configure/）
```

### 获取rml对象
通过ConfigureInterface模块下Configure类的getRml方法来获取当前生效的rml对象
```
RMLObject getRml(Context context, String filename)
```

### 获取rml时的合并策略
当我们要获取filename为test的的rml文件时，内部加载顺序简述如下：

```
1.查找系统通用rml文件
例如：工程根目录/frameworks/Configure/src/main/res/xml/

2.查找产品相关的rml文件（“production_rml_”+“filename”)的xml文件
（如果原filename中已包含此前缀则跳过）
例如：工程根目录/configure/production/？/resource/data/res/xml/production_rml_test.xml

3.查找开发者修改的rml文件
例如：设备/sdcard/ros/configure/test.xml

合并覆盖策略：
后加载的rml文件如果根标签含有override属性且为true，则可完全覆盖之前读取的rml
否则，后加载的rml文件所有子标签会插入到原rml下的第一个位置
```
