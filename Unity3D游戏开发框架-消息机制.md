#EventListener事件监听器
bool HandleEvent（）  //处理消息的方法，如果成功返回false，中断返回true

int EventPriority();     //消息优先级

Awake();   //



#EventNode事件节点

Awake()      //事件节点会将自身放到核心事件节点上，以便核心节点统一发消息

int EventNodePriority()    //事件优先级

Dictionary<int, List<IEventListener>> mListeners；  //所有事件集合

List<EventNode> mNodeList    //消息节点

AttachEventNode(EventNode node)  //将外部传入的消息存入到mNodeList

bool DetachEventNode(EventNode node)   //删除节点

AttachEventListener(int key, IEventListener listener）   //将消息存入到

DetachEventListener(int key, IEventListener listener)   //卸载消息

SendEvent(int key, object param1 = null, object param2 = null)  //发送消息


DispatchEvent(int key, object param1, object param2)   //将消息向子类派发，

TriggerEvent(int key, object param1, object param2)   最后在此调用key对应的mListeners里Evnent的HandleEvent方法





消息发送流程：
 EventNode1.Instance.SendEvent(EventDef.EventTest1, "测试消息发送");


EventNode:
走到 DispatchEvent(key, param1, param2);  //派发消息到子消息节点以及自己节点下的监听器上