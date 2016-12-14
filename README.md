skeleton_detection
===============
ROS骨骼检测程序
功能:启动摄像头读取数据，发布RGBD信息，同时检测人体骨骼，输出所有检测出的骨骼坐标，并将其中置信度最高的用户坐标（头部）以/skeleton_point的topic发布出去。适用于机器人对人体的定位和跟踪。

用到的包：
`openni2_launch`&`openni2_tracker`: ROS上对OpenNI2和NiTE2的封装
`yaml_cpp_0_3`: YAML的C++解释器

### 安装

1. 下载并安装NiTE2.x and OpenNI2 

2. 将NiTE2的库创建链接

    ```bash
	ln -s ~/NITE2.X_PATH/Samples/Bin/NiTE2 ~/.ros/NiTE2
    ```

3. 设置CMakeLists.txt中的路径

    ```bash
	set(OPENNI2_WRAPPER /opt/ros/indigo/include/openni2_camera/)
	set(OPENNI2_DIR ~/OpenNI2/)
	set(NITE2_DIR ~/NiTE-Linux-x64-2.2/)
	set(NITE2_LIB ~/NiTE-Linux-x64-2.2/Redist/libNiTE2.so)
    ```

4. 编译

    ```bash
    cd catkin_ws
    catkin_make
    ```

5. 运行

    ```bash
    roslaunch skeleton_detection tracker.launch
    ```


### 效果
检测到人体的骨骼，发布各关节相对于/map的坐标，并将置信度最高的用户位置发布
![demo](http://github.com/sychaichangkun/skeleton_detection/raw/master/images/pic1.png)

![demo](http://github.com/sychaichangkun/skeleton_detection/raw/master/images/pic2.png)


### THANKS!
Muhannad
https://github.com/OMARI1988/skeleton_tracker
