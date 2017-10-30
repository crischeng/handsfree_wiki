# 4.2 Stone

![Alt text](/images/Mechanical/stone/wiki/stone_small_render.jpg)

## 概述
Stone是一款采用前万向后双驱动轮底盘布局的智能车平台。其整机结构采用平板桁架式透明化设计，外形简单又不失机械美感。Stone可搭载Dobot1、Dobot m1等小型机械臂，能支持多种激光雷达，TX1、TK1、树莓派等主流控制器。其配备高度可调的两轴云台，兼容多款RGBD摄像头和单、双目摄像头。

## 外形及性能参数
机器人参数| 值
------------ | -------------
空重 | 约3kg
直径(cm)  | 36
高度(cm) | 32.2（不加云台） 125.2（加云台）
最大速度(m/s) | 1.2
额定承载能力(kg) |6
支持的传感器 | Rplidar A1/A2，Hokuyo URG-04L/UTM-30Lx，assusxtion，Kinect1/2)
支持的设备 | Dobot机械臂 1/2，HF云台，双目摄像头，单目高清摄像头
支持的控制器 |  TX1，TK1，RK3288，树莓派，pcduino

## 设计特点

![Alt text](/images/Mechanical/stone/Stone_V2.0_turn_around_good.gif)

前置万向轮的两轮驱动方式让车体拥有优越的稳定性；一对775电机加64mm铝合金轮保证了强大前行动力；三层高强玻纤板加8根铝柱组建的骨架在保证承力可靠性的同时以一种简洁明快的方式将各部件一无保留地呈现给使用者。从此，安装、接线、测试、检修，轻车熟路，一目了然。毫无意外，Stone能够支持多种激光雷达，多种控制器（Tk1、Tx1、树莓派等），也可以支持小型机械臂，如Dobot1、Dobot m1。另外，Stone高置的云台能够兼容多款RGBD摄像头和单、双目摄像头，并能提供270度的周向旋转角和180度的俯仰旋转角，让世界一览无余。

## 实验演示

### 基于激光雷达的建图导航避障 (此处采用了Stone的前身Jilong的视频)

![](/images/Experiment/jilong/jilong_navigation_best_compression.gif)

### 基于RGBD的目标跟踪(此处采用了Stone的前身Jilong的视频)

![](/images/Experiment/jilong/jilong_cvdemo_best_comprssion.gif)

### 基于RGBD的建图导航避障 

![](/images/Experiment/stone/stone_navigation_best_compression.gif)

综合来说，Stone已经很好的个人机了，有一定的载重能力，支持Dobot机械臂，适合小实验室和个人机器人研究。但是还不能完成一些复杂的任务，比如抓取一瓶水，开个门，负载也有限，所以有更高需求的请看[Giraffe](https://github.com/HANDS-FREE/HANDS-FREE.github.io/wiki/4.3-Giraffe)，Giraffe有着庞大的身躯和超大的负载能力，可以支持UR5和KUKA的一些工业机械臂，或者配合HandsFree自主设计的低成本ARM，可以胜任大部分的机器人研究任务。

## 安装说明

![Alt text](/images/Mechanical/stone/wiki/stone_small_introduction2.jpg)
![Alt text](/images/Mechanical/stone/wiki/stone_small_introduction1.jpg)
![Alt text](/images/Mechanical/stone/Stone_V2.0_assemble_medium.gif)

###  零件清单
1. 玻纤板五块：底板、中层板、顶板、云台支撑板、激光雷达转接板
2. 万向轮一套，海绵轮两套（包括联轴器），775电机（含减速组和固定架）两套
3. 铝柱16根，铝杆2根（选购）、云台一套（选购）
4. 螺钉、螺母若干（考虑到螺钉、螺母为细小部件，易丢失损耗，特意多配几个以作备用）

### 安装步骤
1. **电机安装**

将电机和L形电机固定架用6个螺钉连接起来，并拧紧螺钉即可

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble1.jpg)

2. **主动轮的安装**

将铝合金主动轮的轮轴套在电机减速箱动力输出轴上，并拧紧轮轴侧面的紧定螺钉即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble2.jpg)

3. **电机在底板上的安装**

将L形电机固定架和玻纤底板通过4对螺钉螺母连接在一起（具体孔位参见附图）

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble3.jpg)

4. **万向轮的安装**

将万向轮和玻纤底板通过四对螺钉、螺母连接在一起。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble4.jpg)

5. **激光雷达的安装**

根据用户手头的激光雷达型号，先将激光雷达安装在激光雷达转接板上（孔位说明见附图）。然后将激光雷达转接板通过4根4*10mm的双通铜柱和8个螺钉连接在玻纤底板上。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble5.jpg)

6. **电机驱动板的安装**

将电机驱动板和玻纤底板通过4根20mm长的铜柱和8颗M4的螺钉连接起来。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble6.jpg)

7. **主控板的安装**

将主控板和玻纤底板通过4根20mm长的铜柱和8颗M4的螺钉连接起来。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble7.jpg)

8. **支撑铝柱的安装**

将两段铝柱通过双头螺柱串联成120mm长的铝柱，再将铝柱和玻纤底板通过M4的螺钉连接。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble8.jpg)

9. **中层板的安装**

使中层板上铝柱通过穿过中层板对应孔位的双头螺柱和底板上铝柱连接，拧紧铝柱，即可将中层板固定在两段铝柱之间。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble9.jpg)

10. **顶板的安装**

使M4的螺钉穿过顶板上对应孔位和中板上铝柱连接，拧紧螺钉，即可将顶板固定在螺钉和铝柱之间。
![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble10.jpg)

11. **法兰的安装**

Stone上多处使用了法兰，此处以顶板上法兰为例介绍安装方法。将法兰和玻纤顶板通过3对螺钉、螺母连接即可。（车体上所有法兰如下）

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble11.jpg)
![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble12.jpg)

12. **铝杆的安装**

将直径19mm的铝杆自上而下依次插入顶层、中层、底层的法兰中，然后拧紧法兰侧边的紧定螺钉即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble13.jpg)

13. **云台板的安装**

先按照第11步的方法将法兰安装在云台板上，再将云台板通过法兰安装在两根铝杆上（使法兰的紧定螺钉穿过铝杆上的螺纹孔）即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble14.jpg)

14. **Xtion的安装**

先将Xtion的耳片插入3D打印的支撑件内，并扣合盖板，然后将3D打印的扣合件通过两对螺钉、螺母固定在云台的U形架上。然后再将支撑件和扣合件扣合在一起即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble15.jpg)

15. **云台的安装**

将云台底板通过4根40mm铜柱和8颗螺钉连接在一起即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble16.jpg)

16. **电源管理的安装**

将电源管理模块下面的四个橡胶脚垫放在玻纤底板对应的孔上，并轻轻用力压紧即可。

![Alt text](/images/Mechanical/stone/wiki/stone_small_assemble17.jpg)

## 附录： 各结构板件安装孔位说明

### 底板:

![Alt text](/images/Mechanical/stone/wiki/stone_small_baseboard.jpg)

### 中板:

![Alt text](/images/Mechanical/stone/wiki/stone_small_middleboard.jpg)

### 顶板:

![Alt text](/images/Mechanical/stone/wiki/stone_small_upperboard.jpg)

### 云台支撑板:

![Alt text](/images/Mechanical/stone/wiki/stone_small_headboard.jpg)

### 激光雷达转接板:

![Alt text](/images/Mechanical/stone/wiki/stone_small_laserboard.jpg)

