#使用characterController控制行走

- 给角色添加characterController组件
- 编写逻辑代码
	  private CharacterController cc;      //角色控制器
	    public int speed = 3;               //速度为3
	    void Awake() {
	        cc = this.GetComponent<CharacterController>();    //得到角色自己的控制器
	    }
		
		// Update is called once per frame
		void Update () {
	        float h = Input.GetAxis("Horizontal");      //AD控制左右运动
	        float v = Input.GetAxis("Vertical");        //ws控制前后运动
	        if(Mathf.Abs(h) > 0.1f || Mathf.Abs(v) > 0.1){   //如果h或者v的绝对值大于0.1，表示按下了移动
	            Vector3 va = new Vector3(-h, 0, -v);       //运动的差值给va
	            transform.LookAt(va + transform.position);    //运动方向+角色位置就是目标方向
	            cc.SimpleMove(va * speed);                 //用角色控制器控制运动速度
	        }
	       
		}