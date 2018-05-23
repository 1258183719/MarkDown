#express基础模板
	var express = require('express');			//引入express模块
	var app = express();						//实例化express
	app.get('/', function(req, res){			//当客户端连接上服务器调用
	    res.send('hello world');				//发送数据给客户端
	});
	app.listen(1337);							//监听1337端口



#引用其他类

	var express = require('express');			//引入express
	var router = express.Router();				//调用express的Router()
	router.get('/login', function(req, res){	//当进入程序后接/login进入
	    return res.send('这里将会是登陆页面');
	});
	router.get('/register', function(req, res){	//当进入程序后接/register进入
	    return res.send('这里将会是注册页面');
	});
	// 其他的账户控制器
	module.exports = router;		//将该类给其他类调用

	//使用时接入127.0.0.1/account进入该类的层级，require指定使用的文件路径
	app.use("/account", require('./routes/account'));


#返回html数据
	app.get('/', function(req, res, next){			//设置接受的路径
	res.set('Content-Type', 'text/html');			//设置发送的数据类型
	//设置数据
	res.send('<html>'+
             '<head>'+
			   '<title>TMY博客</title>'+
             '</head>'+
             '<body>' + 
               '现在的日期是：' + new Date() + 
             '</body>'+
             '</html');
	});

#返回网页数据包
