#Description
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

#How to install
##  1. ��װlinuxϵͳ
### ���������װubuntu
##  2. ��װһЩ��Ҫ�Ļ���
```
$ sudo apt-get update
$ sudo apt-get install ant
$ sudo apt-get install openjdk-7-jdk
$ sudo apt-get install unzip
```
## 3. �����ļ�
```
$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```
## 4. ��ѹ�ļ�
### �½�dol���ļ��� 
```
$ mkdir dol
```
### ��dolethz.zip��ѹ�� dol�ļ�����
```
$ unzip dol_ethz.zip -d dol
```
### ��ѹsystemc
```
$ tar -zxvf systemc-2.3.1.tgz
```
## 5. ����systemc
### ��ѹ�����systemc-2.3.1��Ŀ¼��
```
$ cd systemc-2.3.1
```
### �½�һ����ʱ�ļ���objdir
```
$ mkdir objdir
```
###������ļ���objdir
```
$ cd objdir
```
###����configure(�ܸ���ϵͳ�Ļ�������һ�²��������ڱ���)
```
$ ../configure CXX=g++ --disable-async-updates
```
###����
```
$ sudo make install
```
###��¼��ǰ�Ĺ���·��(�������ǰ����·��������������������)
```
$ pwd
```
##6. ����dol
###����ո�dol���ļ���
```
$ cd ../dol
```
###�޸�build_zip.xml�ļ�,�ҵ�������λ�������˵��������systemcλ�������
```
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
```
###��YYY�ĳ���ҳpwd�Ľ����ע�⣬����  64λ ϵͳ�Ļ�����lib-linuxҪ�ĳ�lib-linux64��
###Ȼ���Ǳ���
```
$ ant -f build_zip.xml all
```
###���ɹ�����ʾbuild successful
###���ſ����������е�һ������
����build/bin/mian·����
```
$ cd build/bin/main
```
###Ȼ�����е�һ������
```
$ ant -f runexample.xml -Dnumber=1
```

#Experimental experience
#### 1. ����ʵ�飬����ֱ�Ӵӿγ�Ⱥ��������ʦ�����úõ�Ubuntuϵͳ����δ���������ϰ�����װVMware������󣬵����ѹ���Ubuntuϵͳ���ǵõ�һ�ο�����Ҫ��������ϵͳ�����򲿷������ļ��޷����С�
#### 2. ���ֺ����ĵ��ĵ���ʱ����ʾ���룬Ӧ���ļ������ΪUTF-8������������ʾ��
#### 3. �ȸ����н϶���ؽ̳̣���������ʵ����Ӧ����Լ��Ļ��������ѯ��ز��ͣ�ע�ض�ϸ�ڵ���⡣
