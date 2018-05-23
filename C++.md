#基础内容
	**打印输出**: cout<<"我是孙文斌"<<endl;     //<<endl的作用是在最后一行进行回车
	**等待执行**system("pause");     //暂停
	
	**输入接收**cin>>a；        //从键盘接收值给a

	#include <iostream>//using namespace std;     //引入标准的命名空间
	 自定义数据类型 
		struct Cli{
	int a_a;
	int b_b; 
	} ;
	- //定义一个类 
	class MyClass{
	public:    //定义两个变量 
	int a_a;
	int b_b;
	public:   //定义两个方法 
	 setA(int a){
	 a_a=a; 
	 } 
	 int getA(){
	 return a_a; 
	 } 
	} ;
	
	main( ) {
		MyClass my;    //实例化类 对象 
		my.setA(500); //设置my的A的变量为500 
		int a=my.getA(); //调用getA()方法 
		cout<<a<<endl;//打印 
	}


#命名空间自定义
	#include <iostream>
	
	namespace NA {
		int as=100;
	}
	using namespace std;           //引入标准命名空间
	using namespace NA::as;
	int main()
	{
	        cout << as;
		system("pause");
	}
#寄存器
	register int a = 10;        //提高代码的效率

#class和struct的区别
###class和struct完成的功能是一样的



#三目运算符

	int a = 10;
	int b = 50;
	int c = 0;
	(a < b ? a : b) = 100;    //如果a小于b，则a=100，否则b=100          （在C语言中不能做左值）
	c = (a < b ? a : b);        //如果a小于b右边就返回a的值，否则反之


#const(使变量或内存地址不可变）
	const int a;    //或者  int const a               设置a不可被修改
	const int *b;   //设置b的内存地址不可被修改
	a=&b;            //把b的内存地址的值给了a，如ffx001，ab用着同一个内存地址
	*a=200;          //把a的内存地址的值改成200，也就是指向的b的内存地址是200   
使用const后的变量会变成一个真正的常量
#define的使用
	#defne a cout<<"哈哈"<<endl;   //改变a的作用		