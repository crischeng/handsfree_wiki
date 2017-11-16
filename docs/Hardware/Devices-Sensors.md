# Devices & Sensors supported by HandsFree

------

Hands Free Team 根据 Hands Free 开源项目的硬件标准设计了一款电源分配板，附带多路开关和多种电源转换功能，满足机器人多样的电力需求。    
支持设备列举如下:

* 上位机: TX1，TK1，MiniPC，树莓派
* 2D雷达: RPLIDAR A1/A2,HOKUYOU 雷达,3irobotics A0602/B0602/C0602等
* 3D传感器: Kinect 1.0,Knect 2.0,Xtion (Pro),Xtion 2.0等
* Dobot机械臂等其他

## HandsFree 支持的上位机

Turtlebot2 上位机使用的是一个PC,我们则是多样化,有非常多的选择,不仅仅支持NVIDIA的TX1,TK1,还支持各种MiniPC,树莓派等.

* NVIDIA的[TX1,TK1](http://www.nvidia.cn/object/embedded-systems-dev-kits-modules-cn.html)等
>NVIDIA Jetson TK1 开发者套件为您提供所需的一切，针对嵌入式系统应用释放 GPU 的潜能。它以革命性的NVIDIA Tegra® K1 SoC 为基础构建，并且使用相同的NVIDIA Kepler™ 计算核心，该核心专为全世界的超级计算机而设计。这为您提供了一款全功能NVIDIA CUDA® 平台，用于快速开发和部署面向计算机视觉、机器人技术、医疗和更多领域的计算密集型系统。NVIDIA 提供整个 BSP 和软件堆栈，包括 CUDA、OpenGL 4.4 和 Tegra 加速的 OpenCV。通过一套完整的开发和分析工具，以及对摄像头和其他外围产品的现成支持，NVIDIA 为您提供理想的解决方案，帮助您在我们的Jetson 嵌入式门户上塑造嵌入式未来。   
> Jetson TX1是NVIDIA第二代嵌入式平台开发者套件，虽然只有信用卡大小，但Jetson TX1 GPU模块的浮点运算能力却达到1 Teraflops，相比Jetson TK1有巨幅提升。如此强大的性能，Jetson TX1显然是智能无人机、机器人最理想的嵌入式解决方案。内建256个CUDA核心的NVIDIA Maxwell GPU，64位ARM A57 CPU，4GB LPDDR4内存、16GB闪存、蓝牙、802.11ac Wi-Fi模块和千兆以太网卡，运行Linux for Tegra操作系统。
* MiniPC,树莓派等
> MiniPC和树莓派可以根据自己对程序的要求自行选择,只要可以使用12V/19V供电就可以.

## 2D雷达

HandsFree 支持多种2D雷达设备,RPLIDAR [A1](http://www.slamtec.com/cn/Lidar/A1)/[A2](http://www.slamtec.com/cn/Lidar),还有[HOKUYOU 雷达](https://www.hokuyo-aut.jp/search/single.php?serial=160),[EAI 雷达](http://www.eaibot.com/product/F4),[3irobotics A0602/B0602/C0602](https://shop455951664.taobao.com/?spm=a1z10.5-c-s.0.0.77770839swikOp)等

## 3D传感器

HandsFree支持的3D传感器也很多,包括了[Kinect系列](http://www.k4w.cn/),[Xtion 系列](https://www.asus.com/3D-Sensor/)等等.

## Dobot机械臂等

HandsFree还支持[Dobot 机械臂](https://cn.dobot.cc/)等,可以实现更多功能.
> DOBOT是由深圳越疆科技有限公司研发的机械臂，号称是全球首款高精度消费机桌面机械臂。在能够完成多种机械臂动作的基础上，它主打的是一张“平民牌”，用于教育的此类机械臂售价仅六七千元，这也是它相比于市场竞争者最叫座的地方。DOBOT机械臂可以灵活翻转挪移，能进行画、写、移动、抓握东西，比如在电脑上打字、写字、画画、使用照相机等。
