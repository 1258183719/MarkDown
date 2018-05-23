#导入步骤
- 导入人物模型
- Animation Type设置为Humanoid
- 点击主角色模型的Rig——config调整模型的骨骼位置
- 点击done进行保存
- 选中所有其他动画模型，Animation Type设置为Humanoid  defintion设置为Copy
- 将主角的骨骼给动画

#让人物拿到武器
将武器捆绑上手部，把武器的方位属性rest


#换装
- 导入模型，设置Animation Type设置为Humanoid
- 通过改变人物的Mesh即可换装（即9宫格标示）

#换装的代码
	  public SkinnedMeshRenderer hande;      //得到SkinnedMeshRenderer组件，用于换装
	    public Mesh[] handArray;          //模型的头部模型数组
	    private int handindex = 0;     //记录点击次数
	    //头切换的代码
		public void Hande(){
	        handindex++;     //次数+1
	        handindex %= handArray.Length;    //次数除去数组的长度得到的余数
	        hande.sharedMesh = handArray[handindex];  //得到数组中的第handindex个Mesh，把它给游戏对象的头部
	    }
- 在外部将hande的部分模型拖入hande，将资源内的头部的Mesh放入数组