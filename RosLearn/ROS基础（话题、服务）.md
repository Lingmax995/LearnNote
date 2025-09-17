## ROS基础（工作空间+话题编程）

工作空间是一个存放工程开发相关文件的文件夹
- src 代码空间
- build ：编译空间
- devel ： 开发空间 
- install ： 安装空间

核心模块：
- ROS基础（工作空间创建、通信编程）
- 机器人系统设计（建模、仿真）
- 机器人感知（视觉、语音处理）
- 高级应用（SLAM、机械臂控制）
- ROS 2.**0新特性**
### 创建工作空间和功能包

#### 创建工作空间

编译位置：**所有编译操作都必须在工作空间根目录下进行**

1. 创建工作空间
```
mkdir -p catkin_ws/src
cd src
catkin_init_workspace
```
- 注意事项：
  
    建议同步操作时使用暂停功能

    所有ROS开发文件都应组织在工作空间内

    工作空间是ROS项目的基础容器

1. 编译工作空间
```
cd catkin_ws
catkin_make
catkin_make install
```
1. 设置环境变量
`source devel/setup.bash`
永久设置：将环境变量添加到~/.bashrc或~/.zshrc配置文件中
CTRL+h ： 显示隐藏文件夹
1. 检查环境变量
`echo $ROS_PACKAGE_PATH`

#### 创建功能包
1. 创建功能包
```
cd src
catkin_create_pkg test_pkg std_msgs rospy roscpp
```
- std_msgs(标准消息类型)

2. 编译功能包
```
cd ~/catkin_ws
catkin_make 
source ~/catkin_ws/devel/setup.bash
```

注：同意工作空间下不允许存在同名功能包
不同空间下，允许存在同名功能包

- package的基本结构
	1. include/package_name/：此目录包含了你所需要库的头文件。
		不要忘记导出功能包清单，因为它们还会被其他功能包所使用。
	2. msg/：如果你要开发非标准消息，请把文件放在这里。
	3. scripts/：其中包括Bash、Python或任何其他脚本的可执行脚本文件。
	4. src/：这是存储程序源文件的地方。
		你可能会为节点创建一个文件夹或按照你希望的方式去组织它。
	5. srv/：这表示的是服务（srv）类型。
	6. CMakeLists.txt：这是CMake的生成文件。
	7. package.xml：这是功能包清单文件。

  - 查看命令：使用env | grep ros命令可以过滤显示所有ROS相关的环境变量
  - 关键变量：最需要关注的是$ROS_PACKAGE_PATH环境变量，它决定了功能包的查找路径顺序
  - 路径组成：该变量包含多个路径，用冒号分隔，如/home/hcx/catkin_ws/src:/opt/ros/kinetic/share


- 工作空间的覆盖机制
  - 同名功能包规则：同一个工作空间下不允许存在同名功能包，但不同工作空间下允许存在同名功能包
  - 查找机制：**ROS运行时通过overlaying机制（工作空间覆盖机制）决定同名功能包的查找顺序**

		env | grep ros //查看ros 的相关环境变量
  - 优先级原则：系统会按照特定顺序查找工作空间中的功能包，优先使用先找到的功能包版本
  - 查找命令：`rospack find roscpp_tutorials`可以查看系统路径下的功能包
  - `catkin_ws rospack find roscpp_tutorials`查看工作空间的功能包




### 话题编程 的实现

##### 创建功能包

```
cd src
catkin_create_pkg learning_topic roscpp rospy std_msgs geometry_msgs turtlesim

```
##### 实现一个发布者
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

##### 配置发布者代码编译规则
![话题cmakelist](/img/话题cmakelist.png)
##### 编译并运行

```
cd ~/catkin_ws
catkin_make
source devel/setup.bash
roscore
rosrun turulesim turtlesim_node
rosrun learning_topic velocity_publish
```

##### hello实例

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
![hello实例](/img/hello实例.png)


##### pyhton实例，用自己创建好的msg文件，进行发布/命令

1. 创建自定义的msg文件
2. 在CMakeLists.txt 和 package.xml 里加好依赖并编译
![msg话题依赖](/img/msg话题依赖.png)
3. 编写发布者节点和订阅者节点


### 服务编程

##### 编写srv文件和依赖

![srv文件和依赖](./img/srv文件和依赖.png)

##### 代码依赖
![服务编程代码依赖](./img/服务编程代码依赖.png)

##### 服务编程结果

![服务编程结果](./img/服务编程结果.png)