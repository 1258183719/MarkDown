	using DG.Tweening;
	public Vector3 myValue = new Vector3(0,0,0);//设置起始位置
		 	//设置动画，第一个myValue2是起始位置，第二个是赋值新的位置,Vector3(10,10,10)结束位置
	void Start () {
	    
        //对变量做一个动画 （通过插值的方式去修改一个值的变化）
	    DOTween.To(() => myValue2, x => myValue2 = x, new Vector3(10,10,10), 2);

	}
		void Update(){
		transform.position=myValue2;
		}


#常用的DOTween方法
	 transform.DOMove(new Vector3(0, 0, 0), 1);//让transfrom从当前位置 动画到 0,0,0的位置 时间为1s (修改的世界坐标)
	transform.DOLocalMove(new Vector3(0, 0, 0), 0.3f);//默认动画播放完成会被销毁
	tweener.SetAutoKill(false);// 把autokill 自动销毁设置为false，不销毁动画让动画可以回放
        tweener.Pause();  //动画暂停，动画不会多次生成
	panelTransform.DOPlayForward();//前放

	 panelTransform.DOPlayBackwards();//倒放

#Form Tween
	transform.DOMoveX(5, 4);//让游戏对象从当前x轴位置运动到5
	transform.DOMoveX(5, 4).From(true);//让游戏对象从5运动到原始位置

#动画属性和事件函数

		Tweener tweener = transform.DOLocalMoveX(0, 2);  //设置运动的位置0是位置，2是需要的时间
	    tweener.SetEase(Ease.OutBounce);//设置动画曲线
	    tweener.OnComplete(OnTweenComplete);//动画结束事件调用函数

#文字替换的动画
    private Text text;
	void Start () {
	    text = this.GetComponent<Text>();
	    text.DOText("接下来，我们进入第二篇章接下来，我们进入第二篇章", 4);
	}

#屏幕震动效果
		 transform.DOShakePosition(1,new Vector3(3,3,0));   //参数1抖动的时间，抖动参数
		
#颜色变化
		text.DOColor(Color.red, 2);//让文本变成红色，用时2f
		text.DOFade(1, 3);//让文本慢慢显示1是透明度，3是时间

#DO tween path设置运动路径