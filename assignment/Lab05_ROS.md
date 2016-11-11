#Ubuntu 14.04环境下配置ROS
##Description
Robot operation system，一套框架，底层提供硬件驱动，软件层面支持通用的文件格式。

## 实验环境
### 1.Ubuntu14.04
### 2.进行配置时要下载相关数据包，请确保有网

## How to install
###  1. 添加source.list,指令如下：
```
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
###  2. 添加keys,指令如下：
```
$ sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
```
### 3. 安装
#### (1)首先确保虚拟机的Debian软件包索引是最新的：
```
$ sudo apt-get update 
```
#### (2)桌面完整版安装： 包含ROS、rqt、rviz、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能
```
$ sudo apt-get install ros-jade-desktop-full
```
#### (3)初始化rosdep:
```
$ sudo rosdep init
$ rosdep update
```
#### (4)环境配置：如果每次打开一个新的终端时ROS环境变量都能够自动配置好（即添加到bash会话中），那将会方便很多
```
$ echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```
#### (5)安装rosinatall:rosinstall 是ROS中一个独立分开的常用命令行工具，它可以方便让你通过一条命令就可以给某个ROS软件包下载很多源码树。 
要在ubuntu上安装这个工具，请运行：
```
$ sudo apt-get install python-rosinstall
```
### 4. 至此，整个安装过程结束，下一步测试下配置是否成功。
## 测试ROS 
### 1. 打开一个终端，输入指令：
```
$ roscore
```
#### 出现以下界面：
![1](https://cloud.githubusercontent.com/assets/19356447/20218384/550fa362-a85f-11e6-9a0f-d5b1e4a731bc.png)
### 2. 打开第二个终端，输入x以下指令，开启一个小乌龟界面：
```
$ rosrun turtlesim turtlesim_node
```
#### 出现以下界面：
![2](https://cloud.githubusercontent.com/assets/19356447/20218397/6e609114-a85f-11e6-8785-456b35c2de51.png)
### 3. 打开第三个终端，输入以下指令，接收键盘输入，控制小乌龟移动。
```
$ rosrun turtlesim turtle_teleop_key
```
### 4. 选中最后打开的Terminal,键盘按下上下左右按键,可看到控制小乌龟移动。
#### 出现以下界面：
![3](https://cloud.githubusercontent.com/assets/19356447/20218406/8191cd7a-a85f-11e6-83ad-ca2f72c8f683.png)
### 5. 打开第四个终端，输入以下指令，可以看到ROS nodes以及Topic等图形展示：
```
$ rosrun rqt_graph rqt_graph
```
#### 出现以下界面：
![4](https://cloud.githubusercontent.com/assets/19356447/20218428/959405cc-a85f-11e6-995b-5e851dd524bf.png)
至此，ROS配置就结束了，从测试中我们也可以看出安装是成功的。
#Experimental experience
#### 1. 本次实验较为简单，基本上就是按照教程复制粘贴，安装过程中要注意细节，不要忽略步骤中出现的错误，不然最后测试时不容易查错。
