#DOL实例分析&编程
## 实验任务
### 1.修改example2，让3个square模块变成2个, tips:修改xml的iterator
### 2.修改example1，使其输出3次方数，tips:修改square.c
## 实验步骤
### 1. example1代码分析
在example1中定义了一个平方进程，具体代码如下：
```
if (p->local->index < p->local->len) {
    DOL_read((void*)PORT_IN, &i, sizeof(float), p);
    i = i*i;
    DOL_write((void*)PORT_OUT, &i, sizeof(float), p);
    p->local->index++;
}
```
首先是对判断条件的分析，p->local->index是指当前的位置，该值被初始化为0；p->local->len为生产者的长度，若满足当前位置小于生产者的长度，则对变量i进行平方运算。
### 2. 修改example1源代码
实验要求输出位i的三次方，所以我们只需要在i平方的基础上再乘以i即可，修改代码如下: 
```
i=i*i*i
```
### 3. 进行编译并运行修改后的代码
#### (1) 修改代码之后要重新编译、运行（sudo ant –f runexample.xml –Dnumber=XXX）XXX是运行example的号码，比如上面是2和1
#### (2) 这里需要注意一点，在运行修改后的代码前，首先需要删除main文件夹下的已存在的example文件，该文件的具体目录为dol/build/bin/main；
#### (3) 运行修改后的代码，需要先进入文件所在目录，指令为cd dol/build/bin/main，运行example1,指令为sudo ant -f runexample.xml -Dnumber=1
### 4. 成功截图：

##  2. 安装一些必要的环境
```
$ sudo apt-get update
$ sudo apt-get install ant
$ sudo apt-get install openjdk-7-jdk
$ sudo apt-get install unzip
```
## 3. 下载文件
```
$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```
## 4. 解压文件
### 新建dol的文件夹 
```
$ mkdir dol
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
