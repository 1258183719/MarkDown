1.导入Behavior Designer插件
2.tools--Behavior Designer--edit		进入编辑界面		

- 给游戏对象 Designer添加：点击游戏对象，在编辑界面右键，add Behavior tree
- 重命名行为的名字：Behavior中设置name


- 使用一个行为树：使用Actions下的Log行为，运行代码时进行输出
- 在Task选择Actions下的Log选择Inspector的Text输入要打印的文字

Actions执行一个动作    Conditionals进行一个判断   Composites其他行为的融合器

Actions中的Idle会一直等待，Wait设置等待时间wait time

- 循环播放行为数：在Behavior Tree中Options勾选Restart Whe Complete



#复杂任务

selector  或    当一个子任务执行完之后，本任务执行完毕，不执行其他子任务，第一个任务失败执行下一个
Sequence  与   当所有子任务全部执行完之后，本任务执行完毕，一个执行失败了，后面不执行

- 条件行为树 Conitionals--Basic--Math
- Float Comparison中设置float比较两个值的大小


#Movement pack 移动行为数

- 控制对象在两点之间巡逻

给游戏对象添加行为 Moment--patrol
Waypoints巡逻点数组
speed运动速度
angular speed旋转速度
Arriveb Distance 接近目标差值
给主角添加NavMeshAgent

- 让对象移动到某点
给游戏对象添加行为 Moment--seek

#查看敌人功能
can See Object   查看的Traget Object目标

#变量 Variables
在Variables中添加变量，可在行为数中进行赋值

Can see object中参数Object In Sight，当目标在视野中，将目标赋值给它

Sequence中设置Abort Type为Lower priority，在其同级任务中，其不满足条件在执行下一任务后，当其满足条件就执行其子条件，中止后面的条件

self中止自身的优先级低的条件
both子条件与同级都可以中止



