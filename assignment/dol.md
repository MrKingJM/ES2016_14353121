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
![6](https://cloud.githubusercontent.com/assets/19356447/20219503/b1714110-a864-11e6-8f2d-18394ebb9729.png)
从上图结果可以看到，生产者长度为20，输出了0-19每个数的三次方。
### 4. example2代码分析
```
<variable value="3" name="N"/>  
```
以上源代码中定义了三个square模块.
### 5. 修改example2源代码
实验只需要输出2个square模块，所以只需要把value的值改为2即可，修改代码如下: 
```
<variable value="2" name="N"/>
```
### 6. 进行编译并运行修改后的代码
运行指令为sudo ant -f runexample.xml -Dnumber=2
### 7. 成功截图：
![7](https://cloud.githubusercontent.com/assets/19356447/20219529/cea0c526-a864-11e6-8ad3-489d7a6fd2eb.png)
### 8. dot文件
#### (1) 在运行成功后，我们可以在dol/build/bin/main/example2的文件夹下，看到example2.dot文件。
#### (2) 安装成功后，我们就可以双击打dot文件了！
#### (3) 最后截图为：
![5](https://cloud.githubusercontent.com/assets/19356447/20219485/a07f4668-a864-11e6-8c00-317d8eb85e5a.png)


#Experimental experience
#### 1. 此次实验比较简单，且实验课TA也详细分析了每个example中的源代码及其实现功能
#### 3. 谷歌上有较多相关教程，接下来的实验中应结合自己的环境，多查询相关博客，注重对细节的理解。
