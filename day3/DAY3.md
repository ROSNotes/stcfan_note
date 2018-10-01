# DAY3
## 上午
× rosopic list 查看话题
× rostopic info/turtle1/pose    查看消息类型
* rostopic echo/turtie1/pose    查看XYZ信息
* rqt        autoscroll动态查看
*          在topic输入框中输入
* roslaunch mx_bringup rbc_camera_launch.launch     启动相机底盘
* rqt_graph    分析机器人工作
* roslaunch mx_bringup rbc_lidar _start.launch      启动雷达底盘
* roslaunch mx_nav gmapping_demo.launch rviz_view:=1    开始扫描雷达
* /tf      坐标系的变换关系
* roslaunch mx_undf gazebo.launch        启动3D模型
* roslaunch turtlebot_gazebo turtlebot_world.launch   启动3D模式虚拟环境
* roslaunch turtlebot_gazebo gmapping_demo.launch     启动生成地图算法
* roslaunch turtlebot_rviz_launchers view_navigation.launch  打开图形化调试工具
* roslaunch turtlebot_teleop keyboard_teleop.launch      启动键盘控制
* gmapping     建图
* 1.启动机器人硬件节点——深度摄像头或激光雷达
* roslaunch mx_bringup rbc_camera_start.launch  
* or
*roslaunch mx_bringup rbc_libar_start.launch
* 2.启动gmapping算法包
* roslaunch mx_nav gmapping_demo.launch
* 在远程计算机上
* 3.roslaunch mx_rviz gmapping_view.launch
* rosrun map_server map_saver     建图保存
