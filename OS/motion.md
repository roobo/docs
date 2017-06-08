# joints
Jelly has three joints:
1. **head**, {@link com.roobo.motionsdk.IJoint.HEAD}. It performs up and down motion of Jelly's head. **Range: -15 ~ 15**
2. **neck**, {@link com.roobo.motionsdk.IJoint.NECK}. It performs circular motion of Jelly's head. Range: **-60 ~ 60**
3. **waist**, {@link com.roobo.motionsdk.IJoint.WAIST}. It performs circular motion of Jelly's waist. Range: **-160 ~ 160**

# joint's wrapper
All joints' motion is wrapped in Class JointMotionRequest{@link com.roobo.motionsdk.JointMotionRequest}
```java
void setJoint(String joint); //select the joint.
void setAngel(int angel); //set the degree to move.
void setSpeed(int speed); //set the max moving speed, the unit is degree per second.
void setAcceleration(int acceleration); //set the acceleration of moving.
```

# MotionSample
### MotionSdk
* JointMotionRequest

As decribed above, It is joint's wrapper
* IMotionExecuteCallback

The listener of motion status

```java
//notify motion starting
void onMotionStart();
//notify motion completed
void onMotionComplete();
//notify motion error
void onMotionError(String errorMsg);
//notify motion stopped
void onMotionStop();
```

* MotionManager

MotionManager is designed to connect the motion service and submit JointMotionRequest.

```java
static MotionManager getInstance(Context c); //Motion manager is singleton

/**
   *  Submit one motion request and set the listener of motion status
   * @param joint motion request wrapper
   * @param callback listener
*/
void executeJointMotion(JointMotionRequest joint, IMotionExecuteCallback callback)

/**
   * Submit multiple motion request and set the listener of motion status
   * @param params motion requests wrapper
   * @param callback listener
*/
void executeMultiJointMotion(List<JointMotionRequest> params, IMotionExecuteCallback callback)
```

### sample

```java
MotionManager motionManager = MotionManager.getInstance(context);

JointMotionRequest headMotionRequest = new JointMotionRequest();
headMotionRequest.setJoint(IJoint.HEAD);
headMotionRequest.setAngel(0); // -15 ~ 15
headMotionRequest.setSpeed(100);
headMotionRequest.setAcceleration(100);

JointMotionRequest neckMotionRequest = new JointMotionRequest();
neckMotionRequest.setJoint(IJoint.NECK);
neckMotionRequest.setAngel(0); // -60 ~ 60
neckMotionRequest.setSpeed(100);
neckMotionRequest.setAcceleration(100);

JointMotionRequest waistMotionRequest = new JointMotionRequest();
waistMotionRequest.setJoint(IJoint.WAIST);
waistMotionRequest.setAngel(0); // -160 ~ 160
waistMotionRequest.setSpeed(100);
waistMotionRequest.setAcceleration(100);

/**
 *  By MotionManager, you can control it to perform the motion one by one or perform all motions at the same time.
 *  And you can also get the status of motion by setting the listener {@link com.roobo.motionsdk.IMotionExecuteCallback}
 *  interface IMotionExecuteCallback {
        void onMotionStart();
        void onMotionComplete();
        void onMotionError(String errorMsg);
        void onMotionStop();
    }
 */
motionManager.executeJointMotion(headMotionRequest, new IMotionExecuteCallback.Stub() {
    @Override
    public void onMotionStart() throws RemoteException {

    }

    @Override
    public void onMotionComplete() throws RemoteException {

    }

    @Override
    public void onMotionError(String errorMsg) throws RemoteException {

    }

    @Override
    public void onMotionStop() throws RemoteException {

    }
});
motionManager.executeJointMotion(neckMotionRequest, null);
motionManager.executeJointMotion(waistMotionRequest, null);
/**
 *  Or you can perform all motions at the same time.
 */
List<JointMotionRequest> requests = new ArrayList<>(3);
requests.add(headMotionRequest);
requests.add(neckMotionRequest);
requests.add(waistMotionRequest);
motionManager.executeMultiJointMotion(requests, null);
```
