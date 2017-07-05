### 配置中心

配置中心是一个预定义的为场景和服务提供数据存储的content provider。配置中心维护一个数据库，针对每个特定的uri维护一张数据表。一般情况下， 数据中心包含如下预置的数据表：
* 全局配置表。全局配置表的Uri为：/GlobalConfig，也可以通过ConfigureInterface访问。全局配置表可以用来存储配置信息，非易失性的数据等。重新启动后数据仍然保留。
* 全局状态表。全局状态表的Uri为：/GlobalStatus，也可以通过ConfigureInterface访问。全局状态表可以用于存储场景或者服务的状态。全局状态表存在于内存当中，不会写入到sdcard。重新启动后数据全部丢失。

#### 访问配置中心
对配置中心的访问可以通过ConfigureInterface来完成。详情请参考：[配置中心规则](configure_rules.md)

#### 自定义配置中心
开发者可以通过编写database.xml来增加自定义数据表。一般情况下，请不要试图覆盖已有的数据表，否则可能会使系统服务无法正常运行。详情请参考：[配置中心规则](configure_rules.md)

