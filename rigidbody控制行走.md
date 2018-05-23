#rigidbody控制行走
	public class Move : MonoBehaviour
	{
	   Rigidbody rigidbody1;
	    public int speed = 3;               //速度为3
	    void Start()
	    {
	        rigidbody1 = this.GetComponent<Rigidbody>();
	    }
	
	    // Update is called once per frame
	    void FixedUpdate()
	    {
	        float v = Input.GetAxis("Vertical");        //ws控制前后运动
	        rigidbody1.velocity = transform.forward * v * 3f;
	        float h = Input.GetAxis("Horizontal");      //AD控制左右旋转
	        rigidbody1.angularVelocity= transform.up * h * 3f;
	       
	    }
	}
