#第四天

##					上午

### 一、打开与操作图片

* 1、cheese  /dev/video0    //video0   or   video1   or   video2    //打开相机

* 2、找一张图片，保存到桌面，保存为：image.jpg

* 3、打开终端，进入桌面下，ls可看到image.jpg

* 4、输入：touch  image_read.py -----创建一个文件

* gedit image_read.py-------打开这个文件

* 5、文件中输入：

* 	import  cv2

* 	img  =cv2.imread(‘/home/intel/Desktop/image.jpg’)

* 	cv2.imshow(‘Display’,img)

* 	cv2.waitkey(0)-----单位ms，0无影响，输入一个数值为显示秒数。

* 	cv2.destroyAllwindows()
* 	6、输入：chomd  +x  image_read.py

* 	./image_read.py-----可能报错，点击一下终端后可能报错，这是执行7

* 7、python  image_read.py------打开图片

* 8、ctrl z-----结束程序

* 9、修改文件image_read.py:

* img  =cv2.imread(‘/home/intel/Desktop/image.jpg’)

* img  =cv2.imread(‘/home/intel/Desktop/image.jpg’,0)0为黑白

* 10、再次执行6、7，得到一张失色图片


* 网页搜索 Opencv,找cv2相关，自学

* cv2.waitkey();
### 二、打开摄像头图像

* 	1、打开终端：touch image1_read.py

* gedit  image1_read.py

* 	2、输入：

* 		import  numpy  as  np

* 		import  cv2

* 		cap =cv2.VideoCapture(1)  //1代表摄像头号，还有0、2、等

* 		while(true):

* 			ret,frame=cap.read()

* 			gray=cv2.cvtColor(frame,cv2.COLOR_BGR2GRAY)  //灰度

* 			cv2.imshow(‘frame’,gray)

* //cv2.imshow(‘frame2’,frame) -----彩色图

* //img90=np.rot90(frame)-----图像转90度

* //cv2.imshow(‘90’,img90)

* 			if cv2.waitKey(1)& 0xFF ==ord(‘q’):
 
* 				break
* 		cap.release()

* 		cv2.destroyAllWindows()

* 	3、python  image1_read.py

* 	4、ls  /dev/Videos --查看摄像头号

### 四、在图片上画一条线

* 	1、打开终端：touch image2_read.py

* gedit  image2_read.py

* 	2、输入：

* 		import  numpy  as  np

* 		import  cv2

* 		#Create a black image   //黑色背景

* 		img=np.zeros((512,512,3),np.uint8)

* 		#Draw a diagonal blue line with thickness of 5 px//画一条长度为5px的蓝线

* 		line=cv2.line(img,(0,0),(511,511),(0,255,0),50)//(0,0)---起点坐标、(511,511)----终点坐*标、(0,255,0)----线颜色、50---线宽

* 		cv2.imshow(‘draw_line’,line)

* 		cv2.waitKey(0)
* 			3、python  image_read.py

### 四---1、线画在视频或摄像头图像上

* 		import  numpy  as  np

* 		import  cv2

* 		cap =cv2.VideoCapture(1)  //1代表摄像头号，还有0、2、等

* 		while(true):

* 			# Capture frame-by-frame

* 			ret,frame=cap.read()

* 			#Our operations on the frame come here

* 			gray=cv2.cvtColor(frame,cv2.COLOR_BGR2GRAY)  //灰度

* 			line=cv2.line(frame,(0,0),(511,511),(0,255,0),50)

* font=cv2.FONT_HERSHEY_SIMPLEX

* cv2.putText(gray,’Hello ros’,(10,500),font,4,(255,255,255),2,cv2.LINE_AA)

* #Display the resulting frame

* cv2.imshow(‘frame’,gray)  

* 			if cv2.waitKey(1)& 0xFF ==ord(‘q’):
				

* cv2.imwrite(‘image.jpg’,img)-----图片另存为一个彩色照片

* 写入到：

* 	cv2.waitkey(0)

* cv2.imwrite(‘image.jpg’,img)

* 	cv2.destroyAllwindows()
* 				break

* 		cap.release()

* 		cv2.destroyAllWindows()


		

### 五、话题

		

* rostopic echo +主题   //查看话题详细信息


##					下午

### 一、发布话题

* 1、建立一个.py文件：rospy_pub.py

* 2、编写：

* /#!/usr/bin/env python

* /# license removed for brevity

* import rospy
* from std_msgs.msg import String

* def talker():

*     		pub = rospy.Publisher('chatter', String, queue_size=10)

*     		rospy.init_node('talker', anonymous=True)//创建一个节点，talker为节点名

*     		rate = rospy.Rate(10) # 10hz

*     		while not rospy.is_shutdown():

*     			hello_str = "hello world %s" % rospy.get_time()

*        			rospy.loginfo(hello_str)//在终端显示信息

*         			pub.publish(hello_str)

*         			rate.sleep()//时间搓，单位s，填数可控制显示间隔

* if __name__ == '__main__':

*     		try:

*         			talker()

*     		except rospy.ROSInterruptException:

*         			pass

* 3、运行.py文件：python  rospy_pub.py-------启动节点
* 4、rostopic  list:

* 	/chatter

* 	/rosout

* 	/rosout_agg

* 5、rostopic  echo chatter-------查看详细信息

### 二、查看节点发布

* 1、rosnode list

* 2、rosnode info /talker_.......-------知道话题，对节点进行猜测

* 3、点开rqt_grach   找到节点

### 三、导入消息

* 1、rostopic  type /turtle1/cmd_vel

* 2、touch  rospy_twist.py

* 3、输入：

* 	import rospy

* 	from geometry_msgs.msg import Twist

* 	pub=rospy.Publisher(‘/turtle1/cmd_vel’,Twist,queue_size=10)
* 	rospy.init_node(‘XWG’)

* 	xuegai_rate=rospy.Rate(5)

* 	while not rospy.is_shutdown():

* 		xue_cmd=Twist()

* 		xue_cmd.linear.x=2

* 		xue_cmd.angula	r.z=2

* 		pub.publish(xue_cmd)

* 		xuegai_rate.sleep() ---使程序睡眠

* 4:设置Twist()的信息

* x=Twist()

* x.linear.x=2-----线速度

* x.angular.z=2-----角速度

* pub.publish(x)

### 五、创立订阅者订阅消息

* #!/usr/bin/env python

* import rospy
* from std_msgs.msg import String

* def callback(data):

*     rospy.loginfo(rospy.get_caller_id() + "I heard %s", data.data)

* def listener():

*     rospy.init_node('listener', anonymous=True)

*     rospy.Subscriber("chatter", String, callback)//订阅一个话题

*     rospy.spin()

* if __name__ == '__main__':

* listener()


### 六、检测小乌龟

* /#!/usr/bin/env python

* import rospy

* from std_msgs.msg import String

* from geometry_msgs.msg import Twist

*	if(xue.lineasr.x>0):

*    		rospy.loginfo(“xiao wu gui dong le”)

*	rospy.loginfo(xue.linear.x)

* def listener():

*     rospy.init_node('listener', anonymous=True)

*     rospy.Subscriber("chatter", Twist, callback)//订阅一个话题

*    rospy.spin()

* if __name__ == '__main__':

*    listener()
* def callback(xue):
