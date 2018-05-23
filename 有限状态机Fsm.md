
#设定状态：
Patrol：巡逻
Chasel：追逐
Attack：攻击
Bead：死亡
FsmState:以上状态的父类
AdvanceFsm:行为管理父类
AIControl:角色行为管理类，挂载到每个实际角色身上

#解析FSMState
字典 map：存储Transition状态和FSMActionID行为
 FSMActionID ID：储存状态行为属性
chaseDistance：追逐距离
attackDistance:攻击距离
arriveDistance:到达目标点距离
- 方法
AddTransition：添加状态
DeletTransition：删除状态
GetOutAction：获取状态对应的行为
FindNextPoint：寻找目标点
Reason：子类需要转换状态时调用
Act:子类执行任务


#实现概述
- 创建行为父类FSMState提供行为属性FSMActionID ID，提供寻找的目标点destPos，wayPoints巡逻目标点，curRotSpeed旋转速度，curSpeed移动速度，追逐攻击巡逻距离，行为字典map存储可以切换的行为，AddTransition添加行为和状态到字典中，GetOutAction传入状态获取行为，Reason进行判断是否可以切换行为，Act执行行为对应的操作。
- Attack  继承FSMState方法构造方法接收Transform数组（无用），初始化actionID该状态的行为ID，移动旋转速度，调用FindNextPoint方法。Reson判断自身与玩家距离，变化做出对应的切换（获取npc身上的AIController组件调用PerformTransition方法传入要跳转的状态，它会获取状态对应的行为并将行为切换）
- FSMBaseFSM状态机的基类，playerTransfrom主角位置，pointList巡逻位置集合，desPos真正要寻找的点，shootRate旋转速度，elapseTime攻击时间间隔。Initialize自身初始化，初始化敌人血量攻击时间间隔旋转速度玩家对象初始化各种状态的状态机。
- AdvanceFSM在FSMBase下一级的类，含有fsmStates集合存储所有状态，currentActionID存储当前行为，currentState存储当前状态，
