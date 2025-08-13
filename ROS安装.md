#### ROS安装
安装方式：实体机安装、虚拟机安装（本文采用）
##### 虚拟机按照流程
1.安装虚拟机软件
2.使用虚拟机软件虚拟一台主机
3.在虚拟机上安装Ubuntu20.04
4.在Ubuntu上安装ROS
5.测试ROS 是否正常运行
————————————————
原文链接：https://blog.csdn.net/2302_77915576/article/details/140907918

————————————————

##### VirtualBox安装

- VirtualBox官网进行安装：[https://www.virtualbox.org/wiki/Downloads]

注：需要安装在默认地址，不然会安装失败	


vmware 安装教程可以参考古月居入门21讲第二
virtualBox安装教程可以参考[https://blog.csdn.net/2302_77915576/article/details/140907918?spm=1001.2014.3001.5506]

目前是20.04.06

##### ROS安装步骤

1.配置ubuntu软件和更新
**首先打开“软件和更新”对话框**
前四个是勾选，后面选择合适的镜像源
![[Pasted image 20250709215415.png]]

2.添加ROS软件源
这里是官方默认的
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
````

2.添加密钥
```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

3.安装ROS
```
sudo apt-get update
```
```
sudo apt-get install ros-noetic-desktop-full
```

4.初始化rosdep
```
sudo rosdep init
```
```
 rosdep update
```

5.设置环境变量
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```
```
source ~/.bashrc
```

6.安装构建依赖
```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
```
sudo apt install python3-rosdep
```

7.小乌龟测试

测试：

输入Ctrl+Alt+T,连续打开三个命令行，分别输入下面三个指令

命令行1输入：roscore

命令行2再输入：rosrun turtlesim turtlesim_node

命令行3再输入：rosrun turtlesim turtle_teleop_key

将鼠标放置在第三个命令行的命令，即可用方向键控制乌龟，按“q”退出


上面参考[https://blog.csdn.net/2302_77915576/article/details/140907918]

##### 中间报错

- rosdep update 出现time out 解决办法
	尝试有效[https://blog.csdn.net/zhanghanningleaf/article/details/114710849]
- rosdep最后解决办法
	采用了博主的办法
	1. 为什么叫rosdepc?
	`rosdepc`，c指的是China中国，主要用于和rosdep区分。
	2. rosdepc和rosdep功能一致吗?
	rosdep官方最新版源码直接修改的，小鱼只动了名称和源地址，将其地址修改为国内[gitee](https://zhida.zhihu.com/search?content_id=176742403&content_type=Article&match_order=1&q=gitee&zhida_source=entity)地址。
	3. rosdepc为什么不会初始化失败?
	因为rosdepc使用的是国内的源，rosdep初始化失败是因为其使用的是[github](https://zhida.zhihu.com/search?content_id=176742403&content_type=Article&match_order=1&q=github&zhida_source=entity)，国内无法访问。[https://zhuanlan.zhihu.com/p/398754989]
- 其他
	参考文档[https://blog.csdn.net/PlutooRx/article/details/127558240]
	上面的文档，重新设置了ros的安装源
	参考文档2[https://developer.aliyun.com/article/1321397]