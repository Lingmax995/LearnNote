ROS = 通信机制 + 开发工具 + 应用功能 + 生态系统

#### ROS 核心概念

##### 节点和节点管理器
- 节点(Node)--执行单元
1. 执行具体任务的进程、独立运行的可执行文件;
2. 不同节点可使用 不同的编程语言，可分布式运行在不同的主机;
3.  节点在系统中的名称必须是唯一的。
- 控制中心节点管理器(ROS Master)
1. 为节点提供命名和注册服务;
2. 跟踪和记录话题/服务通信，辅助节点相互查找、建立连接;
3. 提供参数服务器，节点使用此服务器存储和检索运行时的参数。

##### 话题通信
- 话题(Topic)--异步通信机制
1. 节点间用来传输数据的重要总线;
2. 使用发布/订阅模型，数据由发布者传输到订阅者，同一个话题的订阅者或发布者可以不唯一。
- 消息(Message)--话题数据
1. 具有一定的类型和数据结构，包括ROS提供的标准类型和用户自定义类型，
2. 使用编程语言无关的.msg文件定义，编译过程中生成对应的代码文件。

##### 服务通信
- 服务(Service)-- 同步通信机制
1. 使用客户端/服务器(C/S)模型，客户端发送请求数据，服务器完成处理后返回应答数据
2. 使用编程语言无关的.srv文件定义请求和应答数据结构，编译过程中生成对应的代码文件。
   
![image]([Pasted image 20250727223005.png](https://i-blog.csdnimg.cn/blog_migrate/45e6e66125b56b874d3a8397897535f3.png))
   
##### 参数
- 参数(Parameter)--全局共享字典
1. 可通过网络访问的共享、多变量字典:
2. 节点使用此服务器来存储和检索运行时的参数;
3. 适合存储静态、非二进制的配置参数，不适合存储动态配置的数据。


#### ROS 命令行工具使用

##### 常用命令
- rostopic ：话题相关信息指令
- rosservice：服务相关指令
- rosnode : 所有节点相关信息的指令
- rosparam
- rosmsg
- rossrv

1. roscore : ROS Master 启动命令
2. 启动小海龟仿真器 ：`rosrun turtlesim turtlesim_node` 
3. 启动海龟控制节点：`rosrun turtlesim turtle_teleop_key` 
注 ：
- rqt_graph：,ROS分布式系统中不同进程需要进行数据之间的交互,计算图可以以点的网络形式表现数据交互过程，可制作成计算图
4. 通过rostopic发布指令：
```
rostopic pub -r 10 /turtle1/cmd_vel geometry_msgs/Twist "linear:
  x: 1.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0" 
````
其中分别可以设置线速度和角速度，和速率，当前速率 -r 为10

5. 同过rosservice产生新的海归
```
rosservice  call /spawn "x: 5.0
y: 5.0
theta: 0.0
name: 'turtle2'" 
```
分别为位置在5 5 ，角度为0 产生第二只海归

6. 话题记录
`rosbag record -a O cmd_record`
7. 话题复现
`rosbag play cmd_record.bag`
