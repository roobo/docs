# Scene Switch

roobo OS系统提供了场景切换的通知服务，通过这个服务，可以定制自己的场景切换动画或者实现相关需求。

###实现示例
* 获取ISceneSwitchService
* 设置场景切换回调ISceneSwitcher.Stub，场景切换有两个回调：
	* startSceneSwitch()， 场景开始切换，详见注释
	* stopSceneSwitch()，场景切换结束，详见注释

注：示例中并没有做Binder相关的容错处理，请自行实现。

```java
private ISceneSwitchService mISceneSwitchService;

private void bindSceneSwitchService() {
    IBinder binder = RooboServiceManager.getService(mContext, "ROOBO_SCENE_SWITCH_SERVICE");
    if (binder != null && binder.isBinderAlive()) {
        mISceneSwitchService = ISceneSwitchService.Stub.asInterface(binder);
    }

    if (mISceneSwitchService != null) {
        try {
            mISceneSwitchService.setSwitcher(new ISceneSwitcher.Stub() {
                /**
                 * 场景切换开始
                 * @param fromPkg 当前场景包名
                 * @param toPkg 要启动的场景包名
                 * @throws RemoteException
                 */
                @Override
                public void startSceneSwitch(String fromPkg, String toPkg) throws RemoteException {

                }
                
                /**
                 * 场景切换结束
                 * @param toPkg 已经启动的场景包名
                 * @throws RemoteException
                 */
                @Override
                public void stopSceneSwitch(String toPkg) throws RemoteException {

                }
            });
        } catch (RemoteException e) {
            e.printStackTrace();
        }
    }
}
```
