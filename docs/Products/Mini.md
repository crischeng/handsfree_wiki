# 4.1 Mini

![Alt text](/images/Mechanical/mini/wiki/mini_small_render.jpg)

## 概述
Mini是一款采用前万向后双驱动轮底盘布局的小型机器人。其整机结构采用平板桁架式透明化设计，外形简约大方，能支持多种激光雷达，TK1、树莓派等主流控制器，可搭载assustion、Kinect1 、Kinect2等深度摄像头。Mini体型小、功能强大、性价比高，非常适合入门者开发研究和多机集群应用研究。

## 外形及性能参数
机器人参数| 值
------------ | -------------
空重 | < 2kg
直径(cm)  | 23
高度(cm)|20.4（不加云台） 33.3（加云台）
最大速度(m/s) | 1.2
额定承载能力(kg) |3
支持的传感器 | Rplidar A1/A2，Hokuyo URG-04L/UTM-30Lx，assusxtion，Kinect1/2)
支持的控制器 |  TK1，RK3288，树莓派，pcduino

## 设计特点

![Alt text](/images/Mechanical/mini/HF_mini_turn_around_medium.gif)

23cm直径机身，四层黑色哑光玻纤板（亚克力板），9根10mm直径高强铝柱，12v驱动775电机，mini带来的不仅是体型上的小巧玲珑和机械结构的高可靠度，还有出色的动力学性能和别具一格的机械美感。透明化的结构设计使用户的安装、接线、调试、检修顺手简单。麻雀虽小，五脏俱全，Mini小小的体型上能同时支持多种传感器和主流控制器，能运行HandsFree团队开发的任何软件，是初学者入门及多机集群研究、应用的不二选择。

## 实验演示
Mini 小巧玲珑，售价底，适合学生入门 和 用于研究多机器人协同。然而Mini虽然小，却五脏俱全，在移动，建图，导航，避障方面的效果并不会比Stone 和 Giraffe 差，只是载重小，不能放机械臂，PC，这样就限制了机器人其他方面的研究，所以需要更高平台需求的可以看[Stone](https://github.com/HANDS-FREE/HANDS-FREE.github.io/wiki/4.2-Stone)和[Giraffe](https://github.com/HANDS-FREE/HANDS-FREE.github.io/wiki/4.3-Giraffe)

### 基于深度强化学习的多机器人去中心化避障实验 by [Dorabot](http://www.dorabot.com/) 

![4-13](/images/Experiment/mini/4_13_best_compression.gif)

![4-14](/images/Experiment/mini/4_14_best_compression.gif)

去中心化的多机器人避障（decentralized multi-robot collision avoidance） 目标在与多机器人系统在没有中心服务器规划，甚至机器人间没有通讯的情况下，也能拥有高效， 无震荡（Oscillation-Free）机器人避障行为。可以类比在拥挤的街道上行走的人们。基于handsfree 我们构建了完善的实验平台，在我们的实验中，handsfree极大减少了底层开发的难度，加速了我们实物机器人实验进程。


## 安装说明

![Alt text](/images/Mechanical/mini/wiki/mini_small_introduction.gif)
![Alt text](/images/Mechanical/mini/HF_mini_assemble_good.gif)

### 零件清单
1.玻纤板（亚克力板）五块：一层板、二层板、三层板、四层板、激光雷达转接板
2.万向轮一套，海绵轮两套（包括联轴器），775电机（含减速组和固定架）两套。50mm长铝柱10根，30mm长铝柱4根，20mm长铝柱三根。
3.螺钉、螺母若干（考虑到螺钉、螺母为细小部件，易丢失损耗，特意多配几个以作备用）。

### 组装步骤
1. **电机装配**

首先，将电机和L形电机支架用6个M3的螺钉连接起来即可，记得拧紧螺钉哦。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble1.gif)

然后把海绵轮套在电机输出轴上，拧紧紧定螺钉就可以了。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble2.gif)

2. **将电机安装在二层板上**

如下图，将固定架和二层板通过四对螺钉螺母固定在一起，记住螺钉头要向上。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble3.gif)

左右电机都安装好后，是酱紫的：

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble4.gif)

3. **主控的安装**

主控是通过四个16mm长的铜柱安装到二层板上的：
![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble5.gif)

4. **万向轮的安装**

如图，安装万向轮时只需将其和一层板通过四对M4的螺钉螺母连接即可。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble6.gif)

5. **激光雷达的安装**

将激光雷达安装在激光雷达转接板（支持、、、、、雷达）上后，将激光雷达转接板和一层板通过四根10mm高的铜柱和8个M4的螺钉连接
![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble7.gif)

6.  **第一、二层板的连接**

一、二层板之间通过三个20mm长的铝柱连接。前面的两根铝柱可以通过双头螺柱和二层板上的铝柱连接。既然安装到这里了，就顺便把二层板上的四根80mm（50mm铝柱和30mm铝柱通过双头螺柱串联实现）铝柱竖起来吧。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble8.gif)

7. **第三层板的安装**

第三层板的安装很简单，直接把二层板上的四根铝柱一端拧上双头螺柱，再使螺柱穿过三层板上的四个通孔和三层板上50mm铝柱连接就行了。（注意：要加TK1、树莓派、pcduino的小伙伴需要在安装三层板之前把控制器安装在三层板上）

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble9.gif)

8. **第四层板的安装**

将四颗M4的螺钉穿过顶板上对应的四个孔拧紧在铝柱上即可。

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble10.gif)

9. **电池的安装**

电池通过魔术贴贴在二层板的背面即可。

10. **Xtion的安装**

Xtion需要先通过一个螺钉安装在Xtion支架上。再使支架通过两个501mm铝柱固定在四层板对应的孔位上即可。（Kinect1.0的安装与之类似，只是孔位不同）

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble11.gif)

## 附录： 各结构板件安装孔位说明

###  一层板：

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble12.gif)

###  二层板：

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble13.gif)

###  三层板：

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble14.gif)

###  四层板：

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble15.gif)

###  激光雷达转接板:

![Alt text](/images/Mechanical/mini/wiki/mini_small_assemble16.jpg)
