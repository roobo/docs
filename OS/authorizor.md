## 设备验证服务
所有使用roobo OS的设备必须拿到访问服务的token才能够使用线上服务。线上服务包括语音识别，语义理解，图像识别，云端推送。

### Authorizor
Authorizor提供接口用于读取当前获取的token。token获取需要预先设置sn和public key，每台设备有自己的sn和public key

每次访问云端服务的时候需要通过Authorizor获取最新的token。如果在token的使用过程中发现token失效。可以调用接口重置token。
