## 配置中心规则
配置中心是存储状态和配置信息的地方。通过数据库将各类信息保存下来。配置中心的规则用于数据库定义和数据表的预置数据定义。
### 数据库定义
为了方便开发者创建新的数据表，所有的数据表的定义都放在database.xml中。一个典型的database定义如下：
```xml
<databases version="1">
    <table name="GlobalConfig" file="global_config" clear="false">
        <col name="key" type="varchar"/>
        <col name="value" type="varchar"/>
        <col name="type" type="varchar"/>
    </table>
    <table name="SystemService" file="start_binder_config" clear="false">
        <col name="name" type="varchar"/>
        <col name="package" type="varchar"/>
        <col name="type" type="varchar"/>
    </table>
    <table name="SpeakerConfig" file="speaker_config" clear="false">
        <col name="speaker" type="varchar"/>
        <col name="service" type="varchar"/>
    </table>
    <table name="GlobalStatus" file="global_status" clear="true">
        <col name="key" type="varchar"/>
        <col name="value" type="varchar"/>
        <col name="type" type="varchar"/>
    </table>
    <table name="SceneAttributes" file="scene_attr" clear="false">
        <col name="scene" type="varchar"/>
        <col name="action" type="varchar"/>
        <col name="attr" type="integer"/>
    </table>
</databases>
```
每个table标签定义一个数据表。对于SystemService这张数据表，数据定义文件为start_binder_config.xml。包含三列，字段名为name，package和type。类型是varchar。varchar是sqlite支持的类型。字段类型type中也可以声明其他支持的类型。

### 数据表定义
SystemService定义了系统开机时默认加载的启动项。如下：
```xml
<config>
    <item name="ASR"                        package="com.roobo.asr"                 type="service"/>
    <item name="LOCATION"                   package="com.roobo.location"            type="service"/>
    <item name="ThemeManagerService"        package="com.roobo.theme.service"       type="service"/>
</config>
```
数据定义中的每一行都应该与database.xml中定义的字段匹配。不能匹配的项目将被忽略。

每个字段的值都以字符串表示，实际生成数据库的时候会根据字段类型做转化。
