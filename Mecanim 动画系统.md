#动画与模型的绑定
- 给模型设置模型类型为Humanoid(人型动画）
- 设置阿凡达（骨骼）新建一个骨骼Creat，并绑定好骨骼
- 设置其他动画的模型类型为Humanoid，并且Copy之前的骨骼

#动画设置
- 动画模型的Animations中设置
- Loop Time循环播放 position和后面的Roation勾选后动画不会更改位置信息的值
- Mask中设置遮罩，使人物的某个部分不使用动画

#动画播放的条件
- 设置Bool类型，如run   ani.SetBool("run",true);
- 设置Trigger类型，如Attack    ani.SetTrigger("Attack");
- 设置Int类型，如move。默认设置为1， Greate设置比指定值大时调用，Less设置比指定值小

#动画事件（当动画播放了一定时间后触发）
- 模型动画中有一个Events设置事件
- 设置触发的事件时间区间，如：在0.5F设置事件Attack，0.8F设置事件StopAttack
- 在代码中控制是否能进行控制攻击的播放
		
		bool attack=false;
		  public void  Attack(){
		  attack=true;   //设置可以播放攻击动画
		}
		  public void StopAttack(){
		  attack=fasle;   //设置不可以播放攻击动画
		}

- Exit退出当前动画层，回到初始动画。Any Stay //任何动画状态都可以进入该动画

#动画层级
如果有两个动画层级时，应用动画层级Weight更高的动画层级。如果Weight一样，就播放最新的动画层级（新动画层级默认动画不为空）

#动画融合树
- Create Bend tree
- 在List中添加动画

#遮罩
作用：在人物播放跑步动画的同时播放手部攻击动画
- 新建一个Avatar Mask遮罩
- 在动画层级的Mask上设置遮罩。如：在第一层级去除了人物的上半身运动按下W运动跑步，在第二层级按下W手部攻击照常使用
 
#反向动力学
