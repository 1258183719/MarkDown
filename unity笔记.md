#移动物体的代码
	transform.Translate(Vector3.up * 0.1F,Space.World);    //向上运动，上是整个世界的上
	transform.Translate(Vector3.down * 0.1f);             //向上运动，上是物体的Y轴
	PlayerR.AddForce(new Vector3(0f, JumpSpeen, 0f));      //抛出物体

	rigidbody.MovePosition(Vector2.Lerp(transform.position,targetPosition,1.6f);
#按下按钮的监听
	if( Input.GetKey(KeyCode.W))    //按下去时
	if( Input.GetKeyDown(KeyCode.W)) //一直按下去
	if( Input.GetKeyUp(KeyCode.W))  //提起

#获取物体的局部坐标
transform.position.localPosition;


#获取两个坐标之间的距离
	Vector3.Distance(position1,position2)
#渐渐旋转到目标方向
			//确定我当前角色的方向
            Quaternion targetRotation = Quaternion.LookRotation(destPos - npc.position);//巡逻点位置-Npc位置就是要旋转的角度的四原数
            //npc旋转方法第二部 npc位置=Slerp(npc当前位置,目标位置,旋转的时间)
            npc.rotation = Quaternion.Slerp(npc.rotation, targetRotation, Time.deltaTime * curRotSpeed);
#使用协同让物体进行周期运动
	public class rool : MonoBehaviour {
	    private Vector3 v = new Vector3();     //我们运动物体就是改变Vector3的值，也就是它的xyz的轴的值
	    private float speed = 0.375f;          //设置速度
		void Start () {
	        StartCoroutine(Routine());//刚启动程序的时候我们就要启动该方法，把Routine()传入，该方法只能传该值
	    }
	
	    void FixedUpdate() {   //调用该方法是因为该方法每帧调用一次
	        transform.position += v;      //传值给transform.position运动，运动的方向就是v，每帧调用一次  
	    }
	    IEnumerator Routine() {
	        v.z = speed;  //让z轴以speed的速度运动
	        v.x = 0;      //x轴停止运动
	        yield return new WaitForSeconds(0.5f);    //持续0.5秒    下面以此类推
	        v.z = 0;
	        v.x = -speed;
	        yield return new WaitForSeconds(0.5f);
	        v.z = -speed;
	        v.x = 0;
	        yield return new WaitForSeconds(0.5f);
	        v.z = 0;
	        v.x = speed;
	        yield return new WaitForSeconds(0.5f);
	        StartCoroutine(Routine());     //调用自己的方法，循环
	    }
	}

#使用协同播放音乐
	IEnumerable play(){
			AudioSource.PlayClipAtPoint (v1, transform.position); //播放音乐，文件是v1,在游戏对象上进行播放
			yield return new WaitForSeconds (v1.length);   //设置等待的时间，等待的时间为前音乐播放完后
		}


#切换场景的代码
	Application.LoadLevel("s2d");   //切换到s2d的场景中
	using UnityEngine.SceneManagement;     //第二个是设置头文件
	SceneManager.LoadScene("Main");        //场景跳转


#播放音乐详解
	1.)加入组件Audio--Audio Source，导入音频文件
	2.)Play On Awake打钩表示创建的该游戏对象时就播放，loop循环播放，音量Volume
	
	
	二
	给对象加入代码
	
	public class music : MonoBehaviour {
		public AudioClip Clip;
		// Use this for initialization
		void Start () {
		
		}
		
		// Update is called once per frame
		void Update () {
			if (Input.GetMouseButtonDown(0)) {
				AudioSource.PlayClipAtPoint (Clip, transform.position, 1F);
			}
		}
	}
	
	外部设置好音频路径
	播放即可
	
	
	设置摄像头的音乐开关
	Camera.main.GetComponent<AudioSource> ().Stop ();
	Camera.main.GetComponent<AudioSource> ().Start ();


#unity中使用vs写方法时使用Ctrl+Shift+Q



#单例（游戏切换场景保存数据）
	public class PlayerData
	{
	    private static PlayerData tempPlayerDate;
	
	    public static PlayerData getSingle()
	    {
	        if (tempPlayerDate == null)
	        {
	            tempPlayerDate = new PlayerData();
	        }
	        return tempPlayerDate;
	    }
	
	    public int Gold;
	}
	//此方法存储跳转场景任保存零时数据
	PlayerData.PlayerData.Gold

#触发器的三个方法
	void OnTriggerEnter(Collider varObj)   //触碰时
	 void OnTriggerStay(Collider varObj)   //停留时
	void OnTriggerExit(Collider varObj)    //离开时
	varObj.transform.name         //从触碰器得到名字

#碰撞器的三个方法
	OnCollisionEnter（）    碰撞到物体
       OnCollisionExit     离开物体
       OnCollisionStay     待在物体里面	


#修改另一个类的变量
	varObj.GetComponent<PlayerJump>().JumpSpeen = 1000f;   //找到该类所在的游戏对象，<类名>.变量。
    


#定时后调用ReturnPlane方法
Invoke("ReturnPlane", 1f);

#做出间隔时间攻击的写法
	设置攻击时间的默认值 
	timeBetweenAttacks=0.5f;     //0.f秒攻击一次
	 void Update ()
    {
        timer += Time.deltaTime;   //时间累加给timer

        if(timer >= timeBetweenAttacks)   //如果累加的时间大于攻击间隔时间
        {
           timer=0;     //这里写攻击代码，并且把时间累加器归零
        }
    }

#代码中使用没有打钩的组件
	AudioSource gunAudio = GetComponent<AudioSource> ();


#通过两个指定物体从某点发射至某点
	//拿到bullet游戏对象组件的刚体.速度=（碰到的点（墙）-子弹所在的点）的向量，*5速度乘5
	bullet.GetComponent<Rigidbody> ().velocity = (hit.point - bullet.transform.position)*10;  		对象的位置hit.point

#通过SendMessage调用函数
	Camera.main.SendMessgae("Play");    //得到主摄像机对象，对它发送消息，调用方法
	
	
	public void Play(){};       //被调用

#生成物体设置
	GameObject obj==GameObject.Instantiate(player,new Vector3(0,0,200),Quaternion.identity) as GameObject;
	在此处调用Instantiate方法生成游戏对象，传递参数1，要生成的游戏对象的预设，参数2 位置，3旋转角度Quaternion.identity不旋转，as GameObject是强转成GameObject对象赋值给obj
	
#得到两个坐标点之间的位置
	Vector3 vet=Vector3.lerp(pos1,pos2);    //把得到的中间点给vet
	

#设置游戏对象的父类（常在生成游戏对象时设置）
obj.transform.parent=obj1.transform;

#判断物体是否在摄像机内
	void OnBecameVisible()
	void OnBecameInvisible()
	一个是在物体上的Render在任意一个相机上被渲染时调用，一个是Render在所有相机上都不可见的时候被调用，这里的相机也包括编辑器上的相机。
#给克隆的物体添加组件
	obj.AddCommpent<Rigbody>();


#从资源文件夹拿到资源
	GameObject obj=Resources.Loade<GameObject>("Prefabs/Cube");//寻找Prefabs文件夹内的Cube资源，给obj，作为游戏对象

#销毁物体
	Destory(obj,1);

#拿到游戏对象的父级，并在父级查找其下子对象
	GameObject button=this.transform.parent.Find("Cube").gameObject;

#数据的保存
	 	PlayerPrefs.SetInt("DataFromSave", 1); //DataFromSave表示数据来自保存
	PlayerPrefs.GetInt("DataFromSave");


#隐藏游戏对象：
obj.SetActive(false);//把为选择的角色设置为隐藏

#物体的位置Y轴向上2的高度
 transform.position = new Vector3(transform.position.x, transform.position.y + 2, transform.position.z);


#改变用户的朝向位置
Vector3 v=new Vector3(20,Player.y,20);   //指定好目标位置
transform.LookAt(v);                     //设置朝向目标位置


#hv是wasd和上下左右进行控制，值为0-1
	float h = Input.GetAxis("Horizontal");      //AD控制左右运动
	        float v = Input.GetAxis("Vertical");        //ws控制前后运动

#使用CharacterController控制移动：
  cc.SimpleMove(transform.Forworld*10);                 //使用角色控制器的SimpleMove方法，移动方向为角色的前方，乘速度值

#当需要游戏对象的信息比较多的时候实例化此类进行数据处理
	Private Player p;
	
	void Start(){
	p=this.GetCommpont<Player>();
	}

#保持两个物体固定的距离
	 vr = transform.position - cube.transform.position;   //得到自己与主角的位置差值
	  transform.position =vr+cube.transform.position;   //自己的位置+差值

#获得鼠标中键的值Input.GetAxis("Mouse ScrollWheel");

#围绕某点旋转
	 transform.RotateAround(player.position,transform.right, -rotateSpeed * Input.GetAxis("Mouse Y"));   //参数设置，1中心点，2方向（围绕X轴上下旋转），3角度


#获取物体的旋转值
transform.eulerAngles;

#当鼠标碰到自己的身上的碰撞体的时候调用的函数
void OnMouseOver(){}
void OnMouseExit(){}//离开时

#读取文件
public TextAsset textString;     //获取文本
String string=textString.text;    //读取到了文本信息


.enabled关键字用来禁用脚本
.SetActive启用或禁用对象



InvokeRepeating(函数名称，第一次调用时间，之后调用每次间隔时间)
CancelInvoke（函数名称）停止调用该函数

#关闭场景
Application.Quit ();


#设置父级
			obj3.transform.parent = transform;   //设置特效父级为发射点
            obj3.transform.localPosition = new Vector3(0, 0, 0);   //位置在父级归零
            obj3.transform.localRotation = new Quaternion(0, 0, 0, 0);//旋转在父级归零
#得到父物体下有多少子物体
	transform.childCount;
#得到父物体下子物体
	transform.GetChild(i);
#拿到两个位置的差值
	Vector3.Distance(transform.position,obj.transform.position)<0.3f   //判断是否小于0.3f
	
#设置一个可以序列化的类（unity中，所有的类都要可以序列化才能被外界访问
[System.Serializable]

#UGUI的transform为RectTransform，修改局部坐标localPosition就是UGUI的指定位置

##Cursor.visible = false;  //隐藏光标
	
#上下左右移动镜头
      transform.Rotate( new Vector3(0, Input.GetAxis("Mouse X"), 0));
        if (transform.rotation.x < 0.6) {   //x轴角度不能超过这个值，会翻车
            transform.Rotate(new Vector3(-Input.GetAxis("Mouse Y"), 0, 0));
        }
        
        Vector3 rotation = transform.localEulerAngles;
        rotation.z = 0; // 在这里修改坐标轴的值
        transform.localEulerAngles = rotation;

#向量
- 通过向量移动物体到鼠标点击的位置
物体的位置=物体位置+（鼠标位置-物体位置）.标准化向量为1 

	transofrm.position=transform.position+(mousepos-transform.position).normalized*0.1f;

#控制多个2D精灵的覆盖
- 设置精灵的Sorting layer，越往下，层级越高

public static void LoadScene(int sceneBuildIndex, SceneManagement.LoadSceneMode mode = LoadSceneMode.Single);
public static void LoadScene(string sceneName, SceneManagement.LoadSceneMode mode = LoadSceneMode.Single);

//加载场景的四种重写方式：
1.通过场景名加载
2.通过场景所在的排序位置加载
public static void LoadScene(int sceneBuildIndex, SceneManagement.LoadSceneMode mode = LoadSceneMode.Single);
//多加一个LoadSceneMode属性
3.Single加载场景，关闭之前的场景
4.Additive加载场景不关闭之前场景

Button []AllButton =GetComponentsInChildren<Button>();   //获取所有button组件存在数组中

#设置游戏对象跳转场景时不被删除
	DontDestroyOnLoad(this.gameObject);  



#遥感的开发
	IEndDragHandler（屏幕的抬起监听接口） , IBeginDragHandler（屏幕的拖拽监听接口）

	public void OnEndDrag(PointerEventData eventData) //抬起调用
	public void OnDrag(PointerEventData eventData)  //拖动屏幕时调用
	eventdData.point为点击的位置

#设置值只允许在某个区间



	[Range(0f, 1f)]
    public float mAnimL = 0f;




#运动的物体重置位置
Rig.velocity=Vector.zero;  //速度为0
Rig.angularVelocity=Vector.zero; //角速度为0
Trs.Position=Vector.zero;   //位置为0


#Unity序列化
	[Serializable]
	public class Person
	{
	    public string name;
	    public int age;
	}
	[Serializable]
	public class Persons
	{
	    public Person[] persons;
	}
	public class JsonDemo : MonoBehaviour {
	
		// Use this for initialization
		void Start () {
	        Person p1 = new Person();
	        p1.name = "孙文斌";
	        p1.age = 20;
	        Person p2 = new Person();
	        p2.name = "张三";
	        p2.age = 21;
	        Persons ps=new Persons();
	        Person[] p=new Person[]{p1,p2};
	        ps.persons = p;
	        string s = JsonUtility.ToJson(ps);  //将数据序列化成字符串
		}	

#解析Json
        Persons ps2= JsonUtility.FromJson<Persons>(s);
        Debug.Log(ps2.persons[0].name);




#第三方Josn:LitJosn
- 需要使用LitJson.dll文件
- 在Unity下载
- 将下载的LitJson.dll文件放到unity的Plugins文件夹中

##第一种解析方式与unity自带方式一样
	string s = JsonMapper.ToJson(ps);   //LitJson序列化
	Persons ps2 = JsonMapper.ToObject<Persons>(s);
    Debug.Log(ps2.persons[0].name);



#Bundle Asset
	[MenuItem("Assets/Build AssetsBundle")]         //将该方法放在Assets栏下名字为Build AssetsBundle
    static void BuildAllAssetBundles()          
    {
        string dir = "AssetBundles";        //设置资源的文件夹名
        if (!Directory.Exists(dir))         //如果没有该文件夹
            Directory.CreateDirectory(dir); //创建文件夹
        BuildPipeline.BuildAssetBundles(dir, BuildAssetBundleOptions.None, BuildTarget.StandaloneWindows64);        //通过BuildPipeline.BuildAssetBundles打包参数1文件夹，BuildAssetBundleOptions.None不设置，BuildTarget.StandaloneWindows64资源的平台
    }
#读取
	AssetBundle ab=AssetBundle.LoadFromFile("AssetBundles/w/cube.ab");      //要加载的文件路径
        GameObject GO = ab.LoadAsset<GameObject>("Cube");                       //AssetBundle中获取到Cube对象
        Instantiate(GO, transform.position, Quaternion.identity);               //实例化到游戏场景中


#事件分发
	MethodInfo[] list = this.GetType().GetMethods(BindingFlags.Instance | BindingFlags.Public); //将自身的所有publlic需要实例才能使用的方法存进list集合

		ProtocolHandler handler;                            //接收消息的handler（方法）
            handlerDic.TryGetValue(id, out handler);            //传入id返回本地的处理函数


#角色死亡摔倒
rigidbodies[i].isKinematic = false;   //动作不由rigidbody控制
 collidersToEnable[i].enabled = true; //所有碰撞体启用
animator.enabled = false;  //动画禁用



#Protobuf

	using ProtoBuf; 

	[ProtoContract]		  //设置可被序列化
	public class User  {
    [ProtoMember(1)]       //设置标签
    public int Age { get; set; }  
     [ProtoMember(2)]
    public string Name { get; set; }
     [ProtoMember(3)]
    public string Password { get; set; }
     [ProtoMember(4)]
    public string QQ { get; set; }
	}

#序列化
	User u = new User(){
        u.Age = 20,
        u.Name = "孙文斌",
        u.Password = "sunwen456",
        u.QQ = "1258183719"
        };
	using (FileStream fs = File.Create(Application.dataPath + "/user.bin"))  //制定序列化的对象路径
  	{
	Serializer.Serialize<User>(fs, u);  //<序列化的对象类型>(文件流，对象)
	}


#反序列化
        
	using (var fs = File.OpenRead(Application.dataPath + "/user.bin"))  //制定读取的文件路径
        {
           User user= Serializer.Deserialize<User>(fs);		//将文件流反序列化为对象
        }