## HandsFree OpenRE

![OpenRE Architectural](/images/OpenRE/Embedded_Architectural.jpg)

OpenRE全称Open Source Robot Embedded Library ，  是一个专门为机器人写的、基于STM32系列微处理器的嵌入式开源库。经过不断优化，开源库变得鲁棒和通用，从而独立于平台成为一个专门为机器人而生的一个嵌入式库。

主要目的是搭建一个专门为机器人服务的嵌入式跨平台软件框架，涵盖底层设备驱动，算法库，通信与操作系统组件等，主要涵盖以下内容：

* 封装了许多传感器、存储器、输入输出设备的驱动包，并且采用硬件和驱动包隔离的方式，开发者可以轻易的跨平台移植，比如各种伺服设备、数模舵机、直流三相电机、各种传感器、加速计，陀螺仪、磁力计、超声、 GPS、一些交类互 LCD、触摸屏、 flash、 EEPROM、 SD 卡驱动等。
* 具有已经移植好的操作系统层功能，实时操作系统（ RTOS），图形库（GUI），网络协议（LWIP）， USB 协议，使用者可以根据自己的需求，选择合适的模板进行开发，省去了移植过程的繁琐操作。
* 具有很多机器人有关的算法库、 PID 控制包、机器人运动坐标变换包、卡尔曼滤波包、矩阵运算包、四元数等。
* 支持Linux环境下的makefile + QTCreator + armgcc来进行开发

> 在你正式进行开发之前，你需要准备一些基础知识，会使用linux系统(支持ubuntu 14.04 + ROS indogo ， ubuntu16.04 + ROS kinetic)，会用git github管理自己的代码，会使用qtcretor，详情请看[2.-Robotics-Learning](https://github.com/HANDS-FREE/HANDS-FREE.github.io/wiki/2.-Robotics-Learning)

## OpenRE简述

* 获取OpenRE源码： [OpenRE源码](https://github.com/HANDS-FREE/OpenRE) 

OpenRE库使用makefile + QTCreator + armgcc来进行开发，相信熟悉makefile的都知道它有多方便，至于windows系统的开发者，也是可以配置windows下的makefile + QTCreator + armgcc的环境来开发的，这里也强烈建议开发者学习使用makefile，在构建大规模程序框架的时候显得特别给力。对于只熟悉集成开发环境的开发者，或许认为keil更加的方便，但其实是“会者不难，难者不会”。若是实在不想学习强大的make，你也只需学习OpenRE的操作方法来进行开发。不过HANDSFREE的宗旨第一要义是学习和科研，追求永无止境，不断创新，所以OpenRE就不提供keil的工程文件了。

* 获取makefile的学习资料：[makefile学习资料](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F5_Learning_Data%2Fmakefile&parentPath=%2FHANDSFREE)

OpenRE库还移植了PX4的bootloader，增加了硬件抽象层以适用于不同的电路板，增加了Eigen和Matrix矩阵运算库，对框架和一些包都进行了优化等等。

在你正式进行开发之前，你需要准备一些基础知识，会使用linux系统(支持ubuntu 14.04 + ROSindogo ， ubuntu16.04 + ROSkinetic)，会用git管理自己的代码（同时注册一个github账号），会使用qtcretor。


## OpenRE环境配置
### OpenRE  Toolchain   
关于工具链的配置有两种方式，可以直接用apt-get 安装，如果网速太慢也可以在百度云下载deb包安装。
#### Method1: (recommended)
```
sudo add-apt-repository ppa:terry.guo/gcc-arm-embedded  
sudo apt-get update          
sudo apt-get install openocd  gcc-arm-none-eabi    
sudo usermod -a -G dialout $USER    
sudo apt-get install lib32ncurses5 libtool libusb-1.0 libftdi-dev python python-serial python-empy libpython2.7:i386    
sudo apt-get remove modemmanager    
```
#### Method2:
- get toolchain it in [Development_Toolchain](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F3_Software%2FEmbedded_Development_Toolchain&parentPath=%2FHANDSFREE)
- put these softwares in OpenRE/5_Development_Toolchain     
```
- open a terminal and run: sh install.sh    
- sudo usermod -a -G dialout $USER      
- sudo apt-get install lib32ncurses5 libtool libusb-1.0 libftdi-dev python python-serial python-empy libpython2.7:i386     
- sudo apt-get remove modemmanager    
```

### 代码编译与烧写
用jlink烧写时，由于不同的电路板外部晶振频率可能不一样，所以把A板的固件烧到B板就可能导致死机和锁死，然后下一次烧写的时候就烧不进了，当出现这种情况的时候，方法就是按下板子的复位键(按住不动)，运行烧写指令，一两秒后，松开复位键，就能烧写进去了。

为了确保你不会烧写错误，你先确保每个工程的makefile文件和你的板子是匹配的。这里先介绍每个工程所独有的makefile，下一篇会详细介绍整个库的makefile。

![makefile shotcut](/images/OpenRE/makefile.png)

白色字体是变量，黄色字体是变量值，注释部分是变量的可选值。接下来介绍每一个变量的含义。
* BOARD_TYPE：电路板型号，可选值是HANDSFREE生产的几款电路板（目前是3款，control_unit_mini、control_unit_v1和control_unit_v2）。
* ROBOT_MODEL：是当前使用的机器人的型号，可选值是HANDSFREE发布的几款机器人，（目前是三款，null、jilong、jilong_omni3和stone，null代表无机器人对象，在跑OpenRE简单测试程序的时候使用）。
* ROBOT_SIMULATION_MODE：仿真模式使能，如果enable，将不需要实体机器人，我们在电路板内部虚拟电机的存在。一般情况下都选择disable。
* BOOTLOADER_MODE：BOOTLOADER模式可以让用户直接从串口下载程序，如果disable就需要用jlink下载。目前默认disable。
* PAKG：代表本程序所需要使用到的功能包，在简单测试代码里，只用到了common包。在机器人实现代码里，用到了就相对较多了。如果不是自己开发程序，该部分内容一般不做修改。
* OS_MODULE：操作系统的模式，目前支持UCOSII、UCOSIII。如果裸跑单片机程序，就空着不填。
* THIRDPARTY_MODULE：第三方库的选择，比如矩阵库之类的，如果使用就在这里填上对应的第三方库名称。
在正式烧写前，请确保你之前的makefile都配置对了，主要是ROBOT_MODEL，BOARD_TYPE，BOOTLOADER_MODE这三个变量。

#### 直接使用jlink的SWD模式进行烧写
先编译一个简单的工程验证一下你的开发环境已经配置成功：
* 把makefile的BOARD_TYPE改成你板子的型号，如果你使用的第三方板子，则需要看懂makefile，看后面的配置是不是符合你的板子。
* 插上jlink同时用usb为板子供电。
* 打开一个简单工程的makefile文件所在的目录，该makefile为顶层makefile：
> cd OpenRE/0_Project/examples/handsfree_simple_app/linux
* 接着编译：
> make
* 最后烧录：
> make burn

烧写成功的现象是，板子上的led灯持续闪烁。

*（注：如果是重复烧录同一份代码，从第二遍开始就可以省去make clean和make步骤，直接make burn。但是如果两次烧录之间，有.h头文件被修改，就要先make clean，再make，最终make burn。）*

### Makefile选择不同的机器人与主控的方式
其实在上一节编译与下载章节就已经讲解过了，主要就是修改如下两个变量。
>BOARD_TYPE		?= control_unit_v2

>ROBOT_MODEL   ?= stone

一个是选择电路板的型号，一个是选择机器人的型号。可选项在makefile里面都以注释的形式标示出来了。

*（注：非嵌入式开发者只需看完前两章即可）*
