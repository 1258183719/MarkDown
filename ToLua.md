		LuaState lua = new LuaState();     //获取lua
        LuaFunction luaFunc = null; //获取lua方法
        lua.Start();
        string fullPath = Application.dataPath + "\\MyLua/Demo1";  //lua文件夹
        lua.AddSearchPath(fullPath);   //添加lua的配置路径
        lua.DoFile("ScriptsFromFile.lua");  //执行该文件
        lua.Collect();                      //垃圾回收
        lua.CheckTop();                     //检查栈顶
        luaFunc = lua.GetFunction("test.Show");         //调用lua导出的方法
        if (luaFunc!=null)                          //如果方法存在
        {
            int a = luaFunc.Invoke<int, int>(100);      //指定传入与返回的值
            Debug.Log("数字是"+a);                     
        }

	function luaFunc(num)
	return 100+num
	end
	
	test.Show=luaFunc