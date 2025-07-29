工作空间是一个存放工程开发相关文件的文件夹
- src 代码空间
- build ：编译空间
- devel ： 开发空间 
- install ： 安装空间

### 创建工作空间和功能包

#### 创建工作空间
1. 创建工作空间
```
mkdir -p catkin_ws/src
cd src
catkin_init_workspace
```
2. 编译工作空间
```
cd catkin_ws
catkin_make
catkin_make install
```
3. 设置环境变量
`source devel/setup.bash`
4. 检查环境变量
`echo $ROS_PACKAGE_PATH`

#### 创建功能包
1. 创建功能包
```
cd src
catkin_create_pkg test_pkg std_msg rospy roscpp
```
2. 编译功能包
```
cd ~/catkin_ws
catkin_make 
source ~/catkin_ws/devel/setup.bash
```

注：同意工作空间下不允许存在同名功能包
不同空间下，允许存在同名功能包

### 发布者Publisher 的编程实现

#### 创建功能包

```
cd src
catkin_create_pkg learning_topic roscpp rospy std_msgs geometry_msgs turtlesim

```
#### 实现一个发布者
- c++
	- 初始化ROS节点
	- 向ROS Master注册节点信息：发布的话题名和话题中的消息类型
	- 创建消息数据
	- 按照一定频率循环发布消息
- python
	- 初始化
	- 注册节点信息
	- 创建消息数据
	- 按照一定频率发布信息

#### 配置发布者代码编译规则
```
add_executable(velocity_publisher src/velocity_publisher.cpp)
target_link_libraries(velocity_publisher ${catkin_LIBRARIES})
```
#### 编译并运行

```
cd ~/catkin_ws
catkin_make
source devel/setup.bash
roscore
rosrun turulesim turtlesim_node
rosrun learning_topic velocity_publish
```

#### hello实例

- 创建功能包
```
cd src
catkin_create_pkg ssr_pkg rospy std_msgs
catkin_make
```
- 创建hello_node.py文件
```
#!/usr/bin/env python3

#coding=utf-8

  

import rospy

from std_msgs.msg import String

  

if __name__=='__main__':

rospy.init_node("hello_node")

rospy.logwarn("胡汉三，又回来了")

  

pub = rospy.Publisher("Hello",String,queue_size=10)

  

rate = rospy.Rate(10)

  

while not rospy.is_shutdown():

rospy.loginfo("我要刷屏了")

msg = String()

msg.data = "回来了"

pub.publish(msg)

rate.sleep()

  

#chmod +x hello_node.py 更改文件权限,文件最初没有作为程序运行的权限
```
- 运行程序
```
roscore
rosrun ssr_pkg hello_node.py
```
- 查看结果
```
# 查看话题列表
rostopic list
# 查看话题输出结果
rostopic echo /Hello
# 对结果编码解码
echo -e "\u56DE\u6765\u4E86"

```
![[Pasted image 20250729163723.png]]