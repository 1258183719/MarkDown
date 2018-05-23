#itween设置游戏对象移动轨迹
- 下载导入itween
 
	    Hashtable grgs = new Hashtable();
        grgs.Add("x", 3);    //设置x轴运动速度
        grgs.Add("time", 3);  //设置运动时间
        grgs.Add("delay", 1f);//设置延时时间
        grgs.Add("oncomplete", "onupdatefunction"); //设置运动完调用的代码
        grgs.Add("looptype", "pingpong");  //设置运动模式为来回（乒乓）
        iTween.MoveTo(this.gameObject, grgs);  （运动）
	    Hashtable a = iTween.Hash("x",3,"time",2);   //简化写法
		grgs.Add("easetype",ease);//设置移动模式
		MoveTo运动不受外界影响，MooveBy可以受影响


##基础写法
	iTween.MoveTo(this.gameObject, new Vector3(0,10,0),20);

##设置隐藏
	iTween.FadeTo(this.gameObject, iTween.Hash("time", 2, "delay", 2, "alpha", 0));设置参数1是游戏对象，2是消失需要的时间，3是透明度


