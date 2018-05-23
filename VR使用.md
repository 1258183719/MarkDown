#需要材料
SteamVR，VRTK包

#基本知识
在场景中加入CameraRig预制体（VR用户预制体）
结构：
Controller(left):左手手柄
Controller(right):右手手柄
Camera(head)：头部

#按钮按下关键词
Pressed     按下一半
Released    按下一半释放
TouchStart 当触发器被压缩少量时发出。
TouchEnd   完全抬起
Clicked    一直按着时

#按钮名
Touchpad   圆形按钮
Grip       右侧按钮
Trigger	   底部按钮


#监听按钮事件
[RequireComponent(typeof(SteamVR_TrackedObject))]   //添加组件
public class sickhup : MonoBehaviour {   
	SteamVR_TrackedObject trackedobj;   //追踪设备
    SteamVR_Controller.Device dev;   //监听输入
	void Start () {
        trackedobj = GetComponent<SteamVR_TrackedObject>(); //获取组件
	}
	
	// Update is called once per frame
	void FixedUpdate () {
        SteamVR_Controller.Device dev = SteamVR_Controller.Input((int)trackedobj.index);  //获取输入组件
        if (dev.GetTouch(SteamVR_Controller.ButtonMask.Trigger)) //如果按下的是Trigger按钮
        {
            Debug.Log("按了");
        }  
	if (dev.GetTouchDown(SteamVR_Controller.ButtonMask.Trigger)) //如果按下的是Trigger按钮
        {
            Debug.Log("按下了");
        }  
	if (dev.GetTouchUp(SteamVR_Controller.ButtonMask.Trigger)) //如果按下的是Trigger按钮
        {
            Debug.Log("抬起了");
        }     
	}
}

#抓取
给手柄添加触发器，编写触发代码，触发代码中编写按钮事件
抓取的物品不受重力影响，不受其他力影响，设为手柄的子集
放下监听抬起，以上设为受影响并父级为Null
  void OnTriggerStay(Collider collider)
    {
        if (dev.GetTouch(SteamVR_Controller.ButtonMask.Trigger)) //按下
        {
            collider.attachedRigidbody.isKinematic = true; //不受重力影响
            collider.transform.SetParent (transform);    //设为手柄子物体
        }
        if (dev.GetTouchUp(SteamVR_Controller.ButtonMask.Trigger)) //抬起
        {
            collider.attachedRigidbody.isKinematic = false;  //受重力
            collider.transform.SetParent(null); //去除父物体
            tossObject(collider.attachedRigidbody);  //施加力
        }
    }
    void tossObject(Rigidbody rigidbody)
    {
        rigidbody.velocity = dev.velocity; //获取物体的力
        rigidbody.angularVelocity = dev.angularVelocity;//获取施力角度
    }