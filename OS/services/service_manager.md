## 服务管理器
#### 服务、binder和服务管理器
roobo OS支持三种类型的模块，提供binder供外部应用调用的模块成为服务。实现场景生命周期的模块成为场景，另外一种称为普通模块。 

一个服务需要对外包括接口让其他应用程序使用其能力，这个接口以binder的形式提供。同时，为了让其它应用能够搜索到这个服务的接口，需要存在一个存放所有服务binder的中心，我们称之为服务管理器，每个服务向服务管理器注册自己的binder，索引的名称就是服务的模块名称。  

例如，一个对外提供位置查询的服务，声明自己的名称为“Location”，并且向服务管理器注册自己的binder，则其他应用程序可以通过这个名称搜索到位置服务对外提供的binder，并调用接口。
#### 注册binder
注册binder的动作是在Communicator初始化的时候完成的。详见[通讯服务](communicator.md)
#### 搜索服务
服务管理器提供如下接口：
```java
public static IBinder getService(Context context, final String name)
```
其中，context是Android Context，name是服务名称。如果能够搜索到对应的服务，则返回IBinder，需要根据所要获取的服务binder类型做对应的转换。

#### interface
从上面可知，我们从ServiceManager获取到的服务，都是以Ibinder的形式存在，为了能够使用服务，还需要包含对应的aidl，对IBinder进行转换。

一般情况下，如果一个服务模块对外提供服务，需要对应的实现interface库。一个interface库包含aidl的声明，完成了从IBinder到具体接口的映射，也完成包括诸如binder失效后重新获取服务，服务因为某些原因被杀死后重新注册回调等任务。

有了interface的存在，服务使用起来更加简便。 常见的系统服务，包括Communicator，SceneManager等，都有对应的interface可供使用。