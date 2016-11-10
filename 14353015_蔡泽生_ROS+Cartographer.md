#配置ROS以及cartographer
***
##ROS的配置：
关于ROS的配置，完全就是按照网页上给出的步骤进行操作即可，这里因为操作过了，所以就不截图太多  

1.Setup your sources.list  
>sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  

2.Set up your keys  
>sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116  

3.Installation  
>sudo apt-get update  
>sudo apt-get install ros-kinetic-desktop-full  
>sudo apt-get install ros-kinetic-desktop  
>sudo apt-get install ros-kinetic-ros-base  
>sudo apt-get install ros-kinetic-PACKAGE  
>apt-cache search ros-kinetic  

4.Initialize rosdep  
>sudo rosdep init  
>rosdep update
  
5.Environment setup  
>echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc  
>source ~/.bashrc

6.Getting rosinstall  
>sudo apt-get install python-rosinstall  

7.验证ROS：  
这里因为下面配置了cartographer，所以这里就不单独验证(而且没翻墙师兄给的html根本打不开)

***
##Cartographer的配置：
这个东西的配置需要翻墙，但是也可以不用翻墙的去配置，方法如下：  
1.首先安装ceres solver：  
>git clone https://github.com/hitcm/ceres-solver-1.11.0.git  
>cd ceres-solver-1.11.0/build  
>cmake ..  
>make   
>sudo make install 

2.安装cartographer:
>git clone https://github.com/hitcm/cartographer.git  
>cd cartographer/build  
>cmake .. -G Ninja  
>ninja  
>ninja test  
>sudo ninja install     

这里在ninja的时候会花费很长的一段时间；(= =)

3.安装cartographer_ros：  
使用
>git clone https://github.com/hitcm/cartographer_ros.git  

下载到catkin_ws下面的src文件夹下,然后到catkin_ws下面运行catkin_make即可:
![Image text](https://raw.githubusercontent.com/smie14353015/ES2016_14353015/master/img-folder/img3_1.png);  
这里也需要等待一段时间；  
  
4.下载2D数据：
>https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag 

通过该网页将数据下载到Downloads里面，然后运行即可：
>roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag  

这里需要注意，第一次运行可能会出现如下错误：
![Image text](https://raw.githubusercontent.com/smie14353015/ES2016_14353015/master/img-folder/img3_2.png);  
这时候就需要再次重新输入：
>source ~/catkin_ws/devel/setup.dash  
>rospack profile  

这样就可以运行了；

5.运行结果：  
![Image text](https://raw.githubusercontent.com/smie14353015/ES2016_14353015/master/img-folder/img3_3.png);  
![Image text](https://raw.githubusercontent.com/smie14353015/ES2016_14353015/master/img-folder/img3_4.png);  
因为卡在了第三步的67%的地方，所以这里图片显示的有点问题，但是感觉至应该是安装成功了的；


