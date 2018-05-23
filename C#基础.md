#C#基础
	100 >> 2 //数字对折2次，也就是25
	 Console.WriteLine("hellow world");//打印
	  Console.ReadKey();//让程序等待
	 Console.ReadLine();//接收用户输入的值
	
	  string s = "123";//设置string类型文本
	  int i = Convert.ToInt32(s);//String转int
	  decimal money = 1000m;//金钱类型
	  string ss = @"我是
	                孙文斌";        //@字符串原样输出
	  string k = @"gdgd\好fgdgs";  //使@不成为转义符
	
	
	  const int o = 5;  //设置int类型的o为常量5

#枚举enum
		enum Sex {
		男,
		女
		}
			
	//类中使用枚举型
	 Sex n = Sex.男;     //在这里使用枚举
	
	//使用强制类型转换枚举型成int
	int i=(int)n      //得到的i是0，因为男是在第0个位置

#强制类型转换
	//int转枚举
	 int ie = 1;
	 Sex s = (Sex)ie;//ie是1，得到SEX中为1的值就是女，如果是9，原样输出是9
	 string s = "0";    //设置s初值
	   Sex k=(Sex)Enum.Parse(typeof(Sex), s);//把s强制类型转换成Sex类型，然后给k
	

#结构struct
	//在类的外部
	 public struct Person {
	        public String name;
	       public  int age;
	      public  string sex;
	    }
	
	//在类的内部
	 Person p;
	            p.name = "孙文斌";
	            p.age = 19;
	            p.sex = "男";


#随机数
	Random.Range(0,3);   //随机生成大于等于0小于3的数


#foreach遍历
用于循环一个集合

foreach(int a in list){  // list为int类型的集合，遍历其赋值给a
 Console.WriteLine(a);//打印
}

#虚方法
- 在方法前加入virtual就可以使其成为虚方法，被派生类重写
- 重写虚方法的时候使用override就可以重写此虚方法
示例：
class MyBaseClass{
public virtual string VirtualMethod(){
return "哈哈";
}
}

class Myfunch:MyBaseClass{
public override string VirtualMethod(){
return"哈哈哈";
}
}

#签名相同的方法是指：返回值，参数，方法名都相同

#隐藏方法
- 当子类继承父类后并写了一个与父类同签名的且没有定义为虚方法的方法时，就会隐藏父类的方法
- 示例：
 class A{
public  string VirtualMethod(){
return "哈哈";
}
}

class B:A{
public new string VirtualMethod(){   //用new隐藏
return"哈哈哈";
}
}

B b=new B();
b.VirtualMethod();用的是B类的方法
A b=new B();
b.VirtualMethod();用的是A类的方法

#this和base
this可以访问基类和自己的方法，base只能访问基类
this使不使用都可以

#接口与抽象类的区别
接口是公开的，里面不能有私有的方法或变量，是用于让别人使用的，而抽象类是可以有私有方法或私有变量的，

另外，实现接口的一定要实现接口里定义的所有方法，而实现抽象类可以有选择地重写需要用到的方法，一般的应用里，最顶级的是接口，然后是抽象类实现接口，最后才到具体类实现。

还有，接口可以实现多重继承，而一个类只能继承一个超类，但可以通过继承多个接口实现多重继承，接口还有标识（里面没有任何方法，如Remote接口）和数据共享（里面的变量全是常量）的作用.       
实例：

	interface IListDS<T>
    {
        int GetLength();  //返回一个int类型的值的方法
        void Clear();      //无返回值
        void Add(T item);  //接收一个参数为泛型的方法
        T this[int index] { get; }   //this方法
    }
		Class B<t> : AIListDS<T>{  //继承该接口后必须实现接口内的所有方法
		int GetLength(){return null};  //返回一个int类型的值的方法
        void Clear(){};      //无返回值
        void Add(T item){};  //接收一个参数为泛型的方法
        T this[int index] { get; }   //this方法
	}

#抽象
- 抽象关键字abstract
- 可以定义抽象类和抽象方法
- 抽象类不能被实例化，可以通过抽象类声明类型
- 继承抽象类后必须继承抽象方法
- 可以通过抽象类声明类型
示例：

		abstract class Brid{
		private float speed;
		public void Eat(){   //普通方法可以不必须继承
		
		}
		public abstract void Fly(); //抽象方法，必须继承 
		}
		}
		
		pulic class RedBrid{
		public override void Fly(); //重写方法
		
		  }
		}
		
		public Main{
		public main(){
		Brid brid=new RedBrid();
		}
		}

#密封类和密封方法sealed
当类或者方法设置为sealed时无法继承

- 继承构造方法（默认的构造方法，实例化子类时先调用父类的方法再调用子类的）
		public class A{
		public A(){   //A的构造方法
		
		}
		}
		
		public class B{
		public B():A(){ //继承父类的构造方法。默认存在，可以不写
		
		}
		}


- 继承带参数的构造方法
		public class A{
		public A(string name){   //A的构造方法
		
		}
		}
		
		public class B{
		public B(string name,string name2):A(name){ //继承父类的构造方法。默认存在,把传进来的参数name再给父类A
		
		}
		}


#泛型
- 可以定义多个类型，使用的时候都需要定义类型
	pulbic class ClassA<T>{
	private T a;
	private T b;
	public ClassA(T a,T b){
	this.a=a;
	this.b=b;
	}
	public string tostring(){
	return a+""+b;
	}
	}

	public Class Program{
	public void main(){
	var o1=new ClassA<int>(); //此时才给T定义为int类型
	}
	}

#泛型方法
- 泛型的方法就是用在了返回值上，返回一个不确定的值 

		public T Say<T>(int a,int b){    
		return 
		}

#正则表达式
- 定位元字符
string s="Iam blue";
string res=Regex.Replace(s,"^","开始");  s原字符，^头部，开始是内容
string res=Regex.Replace(s,"$","开始");  s原字符，$尾部，开始是内容


#多态
	A中定义  x(); 方法
	B继承A 定义  i();  方法
	B b=new B();   
	b.x(); //B可以调用A的方法

	A a=b;   //子类可以赋值给父类，不用类型转换就可以调用父类方法，
	但是该类不能调用子类的方法
    B newa=(B)a;  //把父类转换成子类就可调用子类方法

#接口的多态性   
 A为接口，提供say方法
 B继承A，实现say()方法
	
	主函数：
		B p= new B(); //实例化B
	            A a=p;  //p赋值给接口a
	            a.say();   //使用a调用B中实现的say方法

#对象关系
包含关系：可以将对象作为变量进行使用
实例：

	 public class B {
	      public   A a;
	       public  int temp;
	    }

	public class A {
       public  void say()
        {
            Console.WriteLine("呵呵");
            Console.ReadKey();
        }
    }
	
	public B{
	B b = new B();
	 b.temp = 100;
	 b.a = new A();
	 b.a.say();
	}
				
集合关系：可以将对象作为此对象的集合进行使用	



#构造函数
	public class A{
	public A(){
	
	}
	public A(int a){
	 Console.WriteLine("A"+a);
	}
	}


	class Program:A
    {
        static void Main(string[] args)
        {
            Program p = new Program();
            Console.ReadKey();
        }
        public Program() : base(3) {//继承父类的构造函数，并传递一个int参数，调用了父类的带一个int参数的构造函数，父类构造函数会被优先调用
            Console.WriteLine("Program");
        }
    }

#字段与属性
字段就是一个变量
属性提供get set方法给外部使用
 private string name;  //字段
        public String Name {   //属性
            get {
                return name;
            }
            set {
                name = value;
            }
        }

#委托delegate
- 作用：将方法当作参数传递，委托即是一个类型
- 使用：定义委托指向类型，创建实例
- 示例：
	delegate void Invok(int i);  //指向一个参数为一个int类型，且没有返回值的方法
    delegate string say();     //指向一个不带参数，返回值为string的方法

应用：

			//指向一个不带参数且有返回值的方法如：toString
			delegate string GetAStrring();   
            int i = 10;
			//实例化a，指向i的toString方法1
            //GetAStrring a = new GetAStrring(i.ToString);
            a=i.ToString; //指向i的ToString方法2
		   // string s = a();  //a可当作函数进行使用1
            string s=a.Invoke();//a可当作函数进行使用2

应用2：

		delegate string sayage(int i);   //定义委托为接收参数为int类型，返回值为string类型的值
         static void Main(string[] args)
        {
            Student stu = new Student();  //实例化student类
          //sayage say = new sayage(stu.say);  //委托指向stu的say方法（方式1）
		   sayage say=stu.say;   //赋值方式2
		//say委托接收传递的19参数，返回student中的say方法
            Console.WriteLine(say(19));  
            Console.ReadKey();
        }
    }
    public class Student {    //定义类
       //say方法，接收int类型的值，返回string类型的值
        public string say(int i) {
            return "我今年" + i + "岁";
        }
    }

应用三：
 	
	class Program
    {
        public static  string sayh(sayage say)  //将sayage委托当作参数传递
        {

            return say(19);   //返回say委托的返回值
        }
      public   delegate string sayage(int i);  //定义委托
         static void Main(string[] args)
        {
            Program p = new Program();   //实例化类
             sayage sa = p.jia;        //委托指向jia方法
            string s=sayh(sa);           调用sayh方法，传递委托，s接收返回值
            Console.Write(s);
            Console.ReadKey();
        }
       
        public string jia(int i) {
            return (i + 1)+"";
        }
    }

#Action委托（系统定义好的委托）
	public void say(){   //定义一个没有返回值和参数的方法
	Console.WriteLine("呵呵");
	}
	
	Action a=say;  //Action委托接收say方法

默认的Action是不带参数的，可指定参数进行参数传递
	Action<int> a;
	Action <int,string>a;
	
#Func
	public int say(){
	return 100;
	}
	
	Func<int> f=say;   //int表示的是返回值为int类型的参数


	public string look(int a){
	
	return "我今年+a+"岁";
	}

    Func<int,sting> f2=look;

总结：Func中，一个参数时，为返回值，多个参数时，最后一个为返回值，前面的是参数。


#多播委托
			Action a = say;  //委托指向say方法
            a += say2;       //委托指向say和say2方法
            a();             //调用方法

#匿名方法
	//委托接收两个参数为int返回值是int的类，用delegate修饰匿名方法
	Func<int,int,int> a=delegate(int a,int b){   
	return a+b;
	};

#Lambda表达式（匿名方法的扩展）
			Func<int, int, int> a = (i, j) =>
            {
                return j+i;
            };

- 当表达式的参数只有一个时，a就是传递的参数
- 
    Func<int> f = a =>  a + 7;
            Console.WriteLine(f(32));

#事件 Event
		public  delegate void Mydelegate();  //声明委托
        public static  event Mydelegate my2;   //定义事件
        public static  Mydelegate my;   //定义委托

- 猫捉老鼠--观察者设计模式
- 
	    class Program
    {
        static void Main(string[] args)
        {
            Cat c = new Cat();   //实例化猫
            Mouse m1 = new Mouse("jack",c);   //实例化老鼠,将猫传递进来，在内部把老鼠的run方法添加到cat的委托  
            Mouse m2 = new Mouse("jack2", c);
            c.Say();                     //猫叫的时候会执行come委托
            Console.ReadKey();
        }
    }
    class Cat
    {

        public void Say()
        {
            Console.WriteLine("我来了");
            come();   //执行委托，可以用来将所有老鼠的run方法全部执行
        }
        public event Action come;   //委托添加event成为事件，外部不能直接在类的外部触发
    }
    class Mouse
    {
        private String name;
        public string Name
        {
            get
            {
                return name;
            }
            set
            {
                this.name = value;
            }
        }
        public void run()
        {
            Console.WriteLine("我是" + name + "我跑了");
        }
        public Mouse(string name, Cat cat)
        {
            this.name = name;
            cat.come += run;  //获取到猫的实例，给猫的come委托添加方法
        }
    }


#LINQ
- 表达式写法
- 
			//添加对象集合
            var list = new List<Student> { new Student {Name="孙文斌",Age=19 },
            new Student {Name="老大",Age=20 },
            new Student {Name="老二",Age=21 },
            new Student {Name="老三",Age=22 },
            new Student {Name="老四",Age=23 },
            new Student {Name="老五",Age=24 }};
            //LINQ表达式查询，from遍历 m查询出来的每个对象 in在 list集合 where条件 m.Age对象名>21 select返回 m对象 也可以返回m.Name就是名字 
            var res = from m in list where m.Age > 21&&Name=="孙文斌" select m;   //多加一个name判断
            foreach (var item in res)
            {
                Console.WriteLine(item.ToString());
            }

- 扩展方法

	var res = list.Where(test);  //集合调用Where方法传递test方法委托，返回true会存入res	
	//调用的该方法如果学生的年龄大于22就设置为true;
	public static  bool test(Student stu) {
            bool b = false;
            if (stu.Age > 22) {
                b = true;
            }
            return b;
        }

- Lamb表达式
 
				集合调用Where，返回m参数，调用m的Age大于20满足条件返回m
	 var res = list.Where(m => m.Age > 20&&Name=="孙文斌");


- 联合和查询

var res=from m  in list1 from k int list2 where m.Name==k.Name select new{Name1=m,Name2=k};
         遍历list1 和list2 条件为list中的name与2中的name相等输出满足条件的name1和name2;

- 排序orderby
- 表达式
	var res = from m in list where m.Age > 21 orderby m.Age select m;  按找年龄从小到大排序
	 orderby m.Age descending    从大到小排序

- 扩展方法
	var res = list.Where(m => m.Age > 20).OrderBy(m=>m.Age) ;  //后面是排序语法，对象的年龄进行排序
	var res = list.Where(m => m.Age > 20).OrderBy(m=>m.Age).ThenBy(m=>m.Name) ;  //ThenBy第二个条件


#反射
			Student stu = new Student();    //实例化学生类
            Type type = stu.GetType();      //获取学生的Type
            Console.WriteLine(type.Name);   //输出类名


#进程和线程
##异步委托

- 实例1 
- 


	public static void say() {
            Console.WriteLine("呵呵");
        }
			Action a = say;   //委托获取say方法
            a.BeginInvoke(null,null);   //开启线程


- 实例2带参数传递
- 
	public static void say(int i) {
            Console.WriteLine("呵呵"+i);
        }
			Action<int> a = say;   //委托获取say方法
            a.BeginInvoke(100,null,null);   //开启线程

- 委托完整案例
- 

	public static string  say(int i ) {
            Thread.Sleep(10);  //休眠100毫秒
            return "执行完毕";
        }
        static void Main(string[] args)
        {
            Func<int,string> a = say;   //委托获取say方法
         IAsyncResult ia=a.BeginInvoke(100,null,null);   //开启线程,第一个参数为需要传递的参数
            while (!ia.IsCompleted)  //没有执行完就返回false，程序停留在此处循环
            {
                Console.Write(".");
                Thread.Sleep(1);//控制检测频率
            }
            
            Console.WriteLine(a.EndInvoke(ia));  //输出返回值
            Console.ReadKey();
        }


- 等待线程执行完毕的另一种写法 
- 
	//让进程等待1000毫秒，如果1000毫秒内执行完毕返回true，否则false;
	bool isEnd = ia.AsyncWaitHandle.WaitOne(1000);  
            if(isEnd)  //如果执行完毕
                Console.WriteLine(a.EndInvoke(ia));  //输出返回值 

##通过回调判断线程是否执行完毕（不会堵住主线程）

	public static string say(int i)
        {
            Thread.Sleep(10);  //休眠100毫秒
            return "执行完毕";
        }
        static void Main(string[] args)
        {
            Func<int, string> a = say;   //委托获取say方法
            //开启线程,第一个参数为需要传递的参数,倒数第二个是执行完后调用的方法，最后一个参数个回掉函数传递参数，对应下面的ia
            IAsyncResult ia = a.BeginInvoke(100, over, a);
            Console.WriteLine("执行完了吗"); //输出委托返回的值
            Console.ReadKey();
        }

        static void over(IAsyncResult ia)
        {
            //将ia从IAsyncResult类型转换为委托类型a
            Func<int, string> a = ia.AsyncState as Func<int, string>;  
            Console.WriteLine(a.EndInvoke(ia)); //输出委托返回的值
        }
    }
  

##Lamb表达式进行多线程回掉
	public static string say(int i)
        {
            Thread.Sleep(10);  //休眠100毫秒
            return "执行完毕";
        }
        static void Main(string[] args)
        {
            Func<int, string> a = say;   //委托获取say方法
           //开启线程,第一个参数为需要传递的参数,倒数第二个是执行完后调用的方法，最后一个参数个回掉函数传递参数，对应下面的ia
           //ar就是传递的参数，在此处，会传递一个IAsyncResult类型的数据进来给ar
            a.BeginInvoke(100, ar=> {
               Console.WriteLine(a.EndInvoke(ar)); //输出委托返回的值
              
           }, null);
            Console.WriteLine("执行完了吗"); //输出委托返回的值
            Console.ReadKey();
        }

##Thread开启线程
	//下载方法
        public static void Download() {
            Console.WriteLine("开始下载");
            Thread.Sleep(1000); //线程休息1秒
            Console.WriteLine("下载完成");
        }
        static void Main(string[] args)
        {
            Thread t = new Thread(Download); //创建线程
            t.Start();                        //开启线程
            Console.ReadKey();
        

	Thread.CurrentThread.ManagedThreadId; //获取线程ID

- Lamb表达式开启线程
-
	Thread t = new Thread(()=> {
                Console.WriteLine("开始下载" + Thread.CurrentThread.ManagedThreadId);
                Thread.Sleep(1000); //线程休息1秒
                Console.WriteLine("下载完成");
            }); //创建线程
            t.Start();                        //开启线程
 

-多线程传递参数


	//下载方法
        public static void Download(object file) {
            Console.WriteLine("开始下载");
            Thread.Sleep(1000); //线程休息1秒
            Console.WriteLine("下载完成");
        }
        static void Main(string[] args)
        {
            Thread t = new Thread(Download); //创建线程
            t.Start("www.baidu.image");    //开启线程,传递参数
            Console.ReadKey();

- 多线程执行其他类中的方法


		MyThread th = new MyThread("呵呵", "www.aaa.com");//自定义的类
            new Thread(th.DownLoad).Start(); //开启线程，执行类中的方法

#前台线程和后台线程
Thread线程是前台线程，线程池是后台线程，当前台线程执行完毕，后台线程会被强制关闭
	Thread th2= new Thread(th.DownLoad);  //创建线程
            th2.IsBackground = true;     //设置为后台线程
            th2.Start();                 //开启线程

#线程池
	ThreadPool.QueueUserWorkItem(DownLoad,"sas");//开启一个工作线程调用方法，传递参数

#任务执行线程
			Task t = new Task(DownLoad);  //创建任务，后台
           	t.Start();                   //开启任务

			TaskFactory tf = new TaskFactory();   //创建任务工厂
           Task t= tf.StartNew(DownLoad);        //开启任务，赋值给Task，可以进行操作

- 多任务顺序执行
- 


	  public static void DownLoad() {
            Console.WriteLine("开始下载");
            Thread.Sleep(1000);
            Console.WriteLine("下载完成");
        }
        public static void DownLoad2(Task t)
        {
            Console.WriteLine("开始下载");
            Thread.Sleep(1000);
            Console.WriteLine("下载完成");
        }
        static void Main(string[] args)
        {
            Task t1 = new Task(DownLoad);
            Task t2 = t1.ContinueWith(DownLoad2);
            Task t3 = t2.ContinueWith(DownLoad2);
            t1.Start();
            Console.ReadKey();
        }
    }


#锁
作用：在多线程操作一个数据的时候会出现错误，使用死锁锁定某个对象不被其他线程给使用，保证多线程的安全

	  public static void change(object o) {
	            MyThread my=o as MyThread;
	            while (true)
	            {
	                lock (my) {   //判断是否锁住了my对象
	                    my.cahnge();
	                }    //此处解除锁
	              
	            }
	        }
	     
	        static void Main(string[] args)
	        {
	            MyThread mth = new MyThread();   //实例化类
	            Thread th = new Thread(change);   //创建线程
	            th.Start(mth);                 //开启线程
	            Thread th2 = new Thread(change);
	            th2.Start(mth);
	            Console.ReadKey();
	        }
	    }
	    public class MyThread {
	        private int i = 1;
	
	        public void cahnge() {
	            i++;
	            if (i == 1) {
	                Console.WriteLine("出错");
	            }
	            i = 1;
	        }
	    }

#Socket服务器编程

	//服务器端建立Socket，参数1指定为内网，参数2以流作为通讯，参数3指定协议
            Socket tcpServer = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
            //绑定id和端口号
            tcpServer.Bind(new IPEndPoint(IPAddress.Parse("192.168.1.108"),7788));//向系统申请一个可用的端口
            tcpServer.Listen(1000);  //等待连接，最大连接数为1000
            Socket socketClient= tcpServer.Accept();  //暂停线程直到有一个客户端连接上来再进行后面的代码，返回以一个Socket
            string str = "你好！欢迎连接！";
            byte []by= Encoding.UTF8.GetBytes(str);  //字符串转字符数组
            socketClient.Send(by);                   //发送消息给客户端
            Console.ReadKey();


#Socket客户端编程
			//服务器端建立Socket，参数1指定为内网，参数2以流作为通讯，参数3指定协议
            Socket tcpClip = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
            IPAddress ipaddress = IPAddress.Parse("192.168.1.108");//把字符串ip地址转换成IPAddress对象
            EndPoint point = new IPEndPoint(ipaddress, 7788);  //设置ip和端口号
            tcpClip.Connect(point);//建立连接
            byte[] data = new byte[1024];  //创建字符数组进行数据接收
            int length = tcpClip.Receive(data);   //接收服务器的数据，并返回长度
            string message = Encoding.UTF8.GetString(data, 0, length); //将获取到的数据转成字符串，并且截取0到终点
            Console.WriteLine(message);
            Console.ReadKey();

#二进制流序列化
			//序列化关键字[Serializable]

		    MyObject my = new MyObject();   //创建对象实例
            FileStream stream = new FileStream("E:\\StrObj.txt", FileMode.Create, FileAccess.Write,
            FileShare.None);  //创建文件流
            BinaryFormatter formatter = new BinaryFormatter();  //创建BinaryFormatter实例，用于序列化
            formatter.Serialize(stream, my);//Serialize方法将my实例序列化存入stream
            stream.Close();
            FileStream readstream = new FileStream("E:\\StrObj.txt", FileMode.Open, FileAccess.Read,
            FileShare.Read);   //创建文件流
            MyObject my2= (MyObject)formatter.Deserialize(readstream);  //读取文件流并赋值
            readstream.Close();   //关闭流

#SOAP序列化：
			using System.Runtime.Serialization;
			using System.Runtime.Serialization.Formatters.Soap ;


       
            string strobj = "test string for serialization";
            FileStream stream = new FileStream("C:\\StrObj.txt", FileMode.Create, FileAccess.Write ,
            FileShare.None);
            SoapFormatter formatter = new SoapFormatter();
            formatter.Serialize(stream, strobj);
            stream.Close();
            //Deserialization of String Object
            FileStream readstream = new FileStream("C:\\StrObj.txt", FileMode.Open , FileAccess.Read ,
            FileShare.Read );
            string readdata = (string)formatter.Deserialize(readstream);
            readstream.Close();
            Console.WriteLine(readdata);
            Console.ReadLine();



#深拷贝与浅拷贝
深拷贝就是复制第一个对象完全脱离其自身，浅拷贝就是两个对象虽然是复制关系，但两者的值互相影响

	public static T DeepCopyWithReflection<T>(T obj)
        {
            Type type = obj.GetType();

            // 如果是字符串或值类型则直接返回
            if (obj is string || type.IsValueType) return obj;

            if (type.IsArray)
            {
                Type elementType = Type.GetType(type.FullName.Replace("[]", string.Empty));
                var array = obj as Array;
                Array copied = Array.CreateInstance(elementType, array.Length);
                for (int i = 0; i < array.Length; i++)
                {
                    copied.SetValue(DeepCopyWithReflection(array.GetValue(i)), i);
                }

                return (T)Convert.ChangeType(copied, obj.GetType());
            }

            object retval = Activator.CreateInstance(obj.GetType());

            PropertyInfo[] properties = obj.GetType().GetProperties(
                BindingFlags.Public | BindingFlags.NonPublic
                | BindingFlags.Instance | BindingFlags.Static);
            foreach (var property in properties)
            {
                var propertyValue = property.GetValue(obj, null);
                if (propertyValue == null)
                    continue;
                property.SetValue(retval, DeepCopyWithReflection(propertyValue), null);
            }

            return (T)retval;
        }


#反射 
反射获取实例

	public class Student 
    {
        public string name;
        public Student(string name)
        {
            this.name = name;
        }
    }
	Type t = Type.GetType("ConsoleApplication9.Student");
            Object[] obj = new Object[] { "孙文斌" };
            Student s = Activator.CreateInstance(t,obj)as Student;
            Console.WriteLine(s.name);

获取并动态调用方法

    public class Util{
    public static  void GetFunc<T>(T t){
        Type t2 = t.GetType();
    MethodInfo method = t2.GetMethod("GetValue");
    //调用方法的一些标志位，这里的含义是Public并且是实例方法，这也是默认的值
    BindingFlags flag = BindingFlags.Public | BindingFlags.Instance;
    //GetValue方法的参数
    object[] parameters = new object[] { "Hello" };
    //调用方法，用一个object接收返回值
    object returnValue = method.Invoke(t, flag, Type.DefaultBinder, parameters, null);
    }
	}