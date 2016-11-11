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

### 将dolethz.zip解压到 dol文件夹中
```
$ unzip dol_ethz.zip -d dol
```
### 解压systemc
```
$ tar -zxvf systemc-2.3.1.tgz
```
## 5. 编译systemc
### 解压后进入systemc-2.3.1的目录下
```
$ cd systemc-2.3.1
```
### 新建一个临时文件夹objdir
```
$ mkdir objdir
```
###进入该文件夹objdir
```
$ cd objdir
```
###运行configure(能根据系统的环境设置一下参数，用于编译)
```
$ ../configure CXX=g++ --disable-async-updates
```
###编译
```
$ sudo make install
```
###记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
```
$ pwd
```
##6. 编译dol
###进入刚刚dol的文件夹
```
$ cd ../dol
```
###修改build_zip.xml文件,找到下面这段话，就是说上面编译的systemc位置在哪里，
```
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
```
###把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
###然后是编译
```
$ ant -f build_zip.xml all
```
###若成功会显示build successful
###接着可以试试运行第一个例子
进入build/bin/mian路径下
```
$ cd build/bin/main
```
###然后运行第一个例子
```
$ ant -f runexample.xml -Dnumber=1
```

#Experimental experience
#### 1. 本次实验，我是直接从课程群上下载由师兄配置好的Ubuntu系统，并未遇到多少障碍。安装VMware虚拟机后，导入解压后的Ubuntu系统，记得第一次开机后要重新启动系统，否则部分配置文件无法运行。
#### 2. 部分含中文的文档打开时会显示乱码，应将文件编码改为UTF-8，即可正常显示。
#### 3. 谷歌上有较多相关教程，接下来的实验中应结合自己的环境，多查询相关博客，注重对细节的理解。
![图片，哈哈哈](https://cloud.githubusercontent.com/assets/19356447/20218111/e54e2fb8-a85d-11e6-9d5e-7e7a77b33e02.png)
