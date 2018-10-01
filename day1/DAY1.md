# DAY1
## 雷达显示
### 启动底盘
 打开终端1
× 输入命令：
roslaunch mx_bringup rbc_lidar_start.launch
* 打开终端2
× 输入命令：
rviz
### 设置配置
× Fixed Frame->lidar_link
*边界尺寸：laserscan->status->size: 0.05
*添加机器箭头：add->Odometry
*topic->/odom;
×Odometry->covarlance->对号关闭
×Odometry->shape->color->0;25;255
*Fixed Frame->odom


*终止：ctrl c

### 打开相机
#### 方法1
* 打开终端1：roslaunch mx_bringup rbc_lidar_start.launch
* 打开终端2: rviz
*设置：Fixed Frame->camera_rgb_frame
*在终端2输入：rqt
#### 方法2
×打开终端1：roslaunch mx_bringup rbc_camera_launch.launch
* 打开终端2: rqt
### 雷达建图
×终端1：roslaunch mx_bringup rbc_lidar_start.launch
	or	roslaunch mx_bringup rbc_camera_start.launch
*终端2：机器人：roslaunch mx_nav gmapping_demo.launch rviz_view:=1
*	远程终端：roslaunch mx_nav gmapping_demo.launch
×		终端3：roslaunch mx_rviz gmapping_view.launch
*建图保存：rosrun map_server map_saver
### 追踪 
× 颜色追踪：roslaunch mx_bringup opencv3_tracker.launch color:=true
× 人脸追踪：roslaunch mx_bringup opencv3_tracker.launch face:=true
### 跟踪
× roslaunch mx_bringup opencv3_fallower,launch
### 语言控制
× roslaunch voice_bringup voice_bringup.launch
