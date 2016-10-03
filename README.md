# ES2016_14353015
# DOL配置过程

##1.配置C/C++ environment

###直接在Ubuntu的命令指示符页面输入:

>sudo apt-get install g++



##2.手动安装最新版本的java，javac

1.将jdk的压缩包拷贝到Ubuntu上，并解压:

>sudo mkdir java  



2.在终端打开解压的文件夹:

>sudo tar zxvf ./jdk-8u40-linux-x64.gz -C /usr/lib/java  



3.配置环境变量:

>gedit ~/.bashrc  

>*在打开的文件的末尾添加  

>enable jdk environment    

>export JAVA_HOME=/usr/lib/java/jdk8  

>export JRE_HOME=${JAVA_HOME}/jre  

>export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  

>export PATH=${JAVA_HOME}/bin:$PATH  

>*保存退出，然后输入下面的命令来使之生效  

> source ~/.bashrc



4.配置默认JDK:

>    sudo update-alternatives --install /usr/bin/java java /usr/lib/java/jdk8/bin/java 300  

>sudo update-alternatives --install /usr/bin/javac javac /usr/lib/java/jdk8/bin/javac 300  



5.验证是否配置成功:

>java version  





##3.安装ant以及Systemc

1.ant:

>sudo apt-get install ant  



2.systems:  

  该过程同PPT上方法一致，这里就不再叙述;



##4.编译DOL并验证;

![https://cl.ly/0A1t343E2r0f](https://cl.ly/0A1t343E2r0f)



##5.实验感想  

*占无













