# 第二天
## 上午
### 一.用命令行创建含有空格的文件夹
*	1、双引号，单引号
*	2、q\ v(用\+空格代替空格)
### 二.git上传文件到gethub
* git clone网址
* git status //查看待上传文件
* git add .
* 确认提交信息：git commit -am“add day1 note”-----文件上传备注
* git push----提交远程仓库
* 输入账号名或E-mail以及密码
* 上传结束
### 三、海龟
* 启动海龟
* 打卡3 个终端第一个输入roscore
* 第二个输入rosrun 	 turtlesim 	turtlesim_node

* 第三个输入 rosrun turtlesim turtle_teleopkey
* 打开第四个 rqt_graph 查看海龟关系
* 打开第五个 rqt_graph 关闭所有，->一片白
* 点击 plugins Message Publisher 删掉所有（点击减号）
* topic  选择 turtle1/cmd_vel
* type ->Twist
* 点击加号，展开新生成的菜单

* rosservice call/turtle1/
* rosservice call/turtle1/tel


* rostopic pub /turtle1/cmd_vel geometry_msgs/Twist按下tab     //  +内容  //给海龟发内容



## 下午
### 启动小海龟，
* 启动终端，输入rosnode list
* 输入rosnode info /trotkesim查看节点信息
* rosnode 按下两个tab查看帮助
* rostopic list列出话题内容
* rostopic –h查看话题帮助
* rostopic find (type类型)
* rostopic info 话题内容
* rostopic pub /turtle1/cmd_vel geometry_msgs/Twist “linear://发布命令
* rosmsg show geometry_msgs/Twist







### 给话题发消息
* type

* rosmsg show geometry_msgs/Twist 
* rosmsg show geometry_msgs/Pose


* rosrun turtlesim turtlesin_node
#### 创建功能包


* mkdir ros_ws/src –p   //创建文件夹
* cd ros_ws/src/
* //cstin_
* catkin_init_workspace
#### 编译工作空间:
* cd ..
* catkin_make
* 工作空间存放功能包
* 创建功能包
* cd src
* catkin_create_pkg turtlesim_bringup rospy

* cd..
* 可忽略再次编译
* 再次编译（每次修改都需要编译）
* catkin_make
* source devel/setup.bash//添加功能包
* rosrun turtlesim
* cd src/tuetlesim_bringup/


* mkdir launch//写launch文件rtl
* touch gomyturtle.launch
* gedit gomyturtle.launch//编辑launch文件  pkg=”turtlesim”,type=” turtlesim_node”（可执行文件名）
* launch帮忙启动节点
* roslaunch turtlesim_bringup(功能包名称) gomyturtle.launch
* 或者roslaunch 路径


### launch文件
*''' <launch>
* <node  name=”zwbz”  pkg=”turtlesim”  type=”turtlesim_node”  />	
* </launch>'''
