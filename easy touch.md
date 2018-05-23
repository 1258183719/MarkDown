#easy button
- 创建按钮---tools--extensction--adding a new button
- Button properties属性：name按钮名，enable是否启用，actived是否禁用，
- Button position&size属性：Anchor设置锚点，offset设置位置，scale设置大小
- Button Interaction&event监听事件属性：Broadcast Message勾选，void touch(string btnname)  监听按钮点击事件。
- Receiver object设置监听的游戏对象
- Use specific method设置按钮的各种事件

- 事件监听，禁用Broadcast Message，代码中使用EasyButton.On_ButtonDown += touch;把方法加入到事件中

#虚拟摇杆
Dynamic joystick勾选后摇杆位置随意更改
Free area选择摇杆只能在指定位置出现
监听joystick：
 Debug.Log(easy.JoystickAxis);