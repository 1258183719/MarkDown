#Demo1ContextView
继承ContextView，用于在Awake方法中启动StrangIoc框架：
this.context = new Demo1Context(this);

#Demo1Context
继承MVCSContext，用于绑定映射：
	protected override void mapBindings()//进行绑定映射 
    {
        //model
        injectionBinder.Bind<ScoreModel>().To<ScoreModel>().ToSingleton();  //将

        //serivce
        injectionBinder.Bind<IScoreService>().To<ScoreService>().ToSingleton();//ToSingleton()表示这个对象只会在整个工程中生成一个

        //command
        commandBinder.Bind(Demo1CommandEvent.RequestScore).To<RequestScoreCommand>();//将
        commandBinder.Bind(Demo1CommandEvent.UpdateScore).To<UpdateScoreCommand>();

        //mediator 
        mediationBinder.Bind<CubeView>().To<CubeMediator>();//完成view和mediator的绑定

          
        //绑定开始事件 一个startcommand
        commandBinder.Bind(ContextEvent.START).To<StartCommand>().Once();
    }
继承父类的构造方法：
public Demo1Context(MonoBehaviour view) : base(view) { }

#Service模块
IScoreService接口：
	void RequestScore(string url);//请求分数
    void OnReceiveScore();//收到服务器端发送过来的分数
    void UpdateScore(string url, int score);

    IEventDispatcher dispatcher { get; set; }

ScoreService继承IScoreService，实现具体的代码：
	public void RequestScore(string url)   //实现具体的接收分数
    {
        Debug.Log("Request score from url : " + url);

        OnReceiveScore();
    }

    public void OnReceiveScore()     //实现发送分数
    {
        int score = Random.Range(0, 100);
        dispatcher.Dispatch(Demo1ServiceEvent.RequestScore,score);
    }

    public void UpdateScore(string url, int score)      实现更新分数
    {
        Debug.Log("Update score to url : " + url + " new score : " + score);
    }

    [Inject]
    public strange.extensions.dispatcher.eventdispatcher.api.IEventDispatcher dispatcher { get; set; }