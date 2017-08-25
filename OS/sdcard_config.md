## 在SDCARD上增加规则

### 增加规则

规则文件位于frameworks/Configure工程的res文件夹下。除非重新编译整个工程，该位置的配置文件不能被修改。

但是我们可以通过在sdcard上放置同名文件，实现增加新的项目到已有的规则当中。

sdcard配置文件的路径是：**ros/configure/**

目前已经支持的配置文件包括：
* pre_process.xml
* post_process.xml
* focus_array.xml
* product_config.xml
* production_service.xml
* production_scene_attr.xml

上述配置文件均为用户可定义的配置文件。原则上不建议覆盖系统内置的配置文件。系统内置的配置文件以roobo开头。

### 通过增加规则实现规则覆盖

对于上述配置文件中的某些，因为规则解析的逻辑被设计为对同名配置项，只识别第一个，忽略随后的同名配置项。所以我们可以通过增加同名规则实现规则覆盖。

*同名规则实现覆盖效果并不针对所有配置文件都生效*

目前能够支持同名覆盖的配置文件有：

* pre_process.xml
* post_process.xml
* focus_array.xml
* product_config.xml