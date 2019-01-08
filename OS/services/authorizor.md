## 设备验证服务
所有使用roobo OS的设备必须拿到访问服务的鉴权信息才能够使用线上服务。线上服务包括语音识别，语义理解，图像识别，云端推送。

### Authorizor
Authorizor提供接口用于读取当前获取的鉴权信息。可用的接口如下：
```java
public static boolean renewToken(Context context);

public static String getToken(Context context);

public static String getClientId(Context context);

public static String getAppId(Context context);

public static String getProduction(Context context);

public static String getDeviceId(Context context);
```
由于鉴权信息会自动更新，所以建议每次访问云端接口的时候获取最新的鉴权信息，确保鉴权成功。
