# 4.3 Giraffe

![Alt text](/images/Mechanical/giraffe/good/Giraffe_big_render1.JPG)
![Alt text](/images/Mechanical/giraffe/good/Giraffe_big_render2.jpg)

## 概述
Giraffe是一款采用前万向后双驱动轮底盘布局的智能车平台。其整机结构采用平板桁架式封闭式设计；侧板采用带磁吸可开合设计；传动系统采用同步带传动。Giraffe可同时支持一前一后两个激光雷达，兼容TX1、TK1、树莓派等主流控制器，配备高度可调、能兼容多款RGBD摄像头和单、双目摄像头的两轴云台。Giraffe可搭载HF Arm1等中型机械臂（总量15Kg左右），具有高达30Kg的承载能力。

## 外形及性能参数
机器人参数| 值
------------ | -------------
空重 | < 12kg
直径(cm) | 38
高度(cm) | 33.2（不加云台） 126.2（加云台）
最大速度(m/s) | 1.6
额定承载能力(kg) | 30 kg
支持的传感器 | Rplidar A1/A2，Hokuyo URG-04L/UTM-30Lx，assusxtion，Kinect1/2)
支持的设备 | HandFree arm，Dobot机械臂 1/2，HF云台，双目摄像头，单目高清摄像头
支持的控制器 |  笔记本，TX1，TK1，RK3288，树莓派，pcduino

## 实验演示

Giraffe在建图导航避障方面的效果和Stone Mini一样，这里就主要展示一下大型机械臂的3D运动规划和抓取，Giraffe是目前HandsFree功能最全，性能最强的平台，也是HandsFree Team目前研究机器人领域的主要实验平台。

![](/images/Experiment/giraffe/giraffe_grab_best_compression.gif)

## 设计特点

![Alt text](/images/Mechanical/giraffe/HF_Giraffe_turn_around_medium.gif)

全身通体的黑色让Giraffe像黑衣武士一样暗暗地透露出一股邪酷。全封闭式的结构让其有一种不可言状的神秘。不过不要担心，Giraffe的左右侧板和后侧板皆采用了门式的开合结构。门侧采用了磁吸设计，让门的开合变得随意起来，从而让用户能轻易地走进这个黑武士的“内心”，感受其精细的内在。传动系统中同步带的传动方式使电机能精确地将转动位移传递给轮轴，也优化了底盘承力形式，使Giraffe拥有多达30公斤的载重能力。Giraffe能够同时支持前后两个激光雷达，同时能兼容多种控制器（Tk1、Tx1、树莓派等）。健壮的身板使其能够搭载大、中型机械臂，从而使其更具实用能力。高高立起地云台是它不屈的头颅，也给它赢得了“Giraffe（长颈鹿）”这一名号。这个“头颅”上可以支持多款RGBD摄像头和单、双目摄像头，使其能轻易而精确扑捉到自己“指尖”的动作，完成主人交给它的各项指令。

### 安装步骤

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_introduction2.jpg)
![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_introduction1.jpg)
![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_introduction3.jpg)

### 零件清单
1. 玻纤板十块：底板、中层板、顶板、云台支撑板、激光雷达转接板（2个）、侧缘板（4个）；亚克力板四块：前侧板、左侧门、右侧门、后侧门。
2. 万向轮一套，铝合金轮两套，电机（含减速组和固定架）两套，轮轴两根，轴承座4个，同步带轮4个，同步带两条。
3. 铝柱32根，铝杆2根（选购）、云台一套（选购）
4. 螺钉、螺母若干（考虑到螺钉、螺母为细小部件，易丢失损耗，特意多配几个以作备用）。

### 装配步骤 
1. **轮轴、同步带轮与轴承座的安装:**

将轴穿过两个轴承座上的轴孔与同步带轮形成轴孔配合，并拧紧同步带轮上的紧定螺钉（先不要拧紧轴承座上的紧定螺钉）。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble1.jpg)

2. **轮轴和主动轮的安装**

将轮轴大头一端插入了轮的中心孔中，再拧紧轮外侧的拉紧螺钉即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble2.jpg)

3. **主动轮在玻纤底板上的安装**

将轴承座和玻纤底板通过四对螺钉螺母连接起来，然后拧紧轴承座上的紧定螺钉即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble3.jpg)

4. **电机、电机固定架和同步带轮的安装**

先将电机和电机固定架通过4个螺钉连接，再将同步带轮安装在电机轴上，并拧紧紧定螺钉。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble4.jpg)

5. **电机的安装**

将电机通过四对螺钉、螺母安装在玻纤底盘的槽孔上，注意稍将螺钉拧紧即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble5.jpg)

6. **同步带的安装**

将同步带套在电机和轮轴的同步带上，你可能需要前后调节电机位置，才能将同步带顺利安装好，然后需要调节电机位置使同步带张紧。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble6.jpg)

7. **万向轮的安装**

将万向轮和玻纤底板通过四对螺钉、螺母连接，拧紧螺钉即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble7.jpg)

8. **电机驱动板的安装**

将电机驱动板通过4根20mm长的铜柱和8颗螺钉连接在玻纤底板上。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble8.jpg)

9. **主控板的安装**

将主控板通过4根20mm长的铜柱和8颗螺钉连接在玻纤底板上。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble9.jpg)

10. **前激光雷达的安装**

首先将现有的激光雷达安装在激光雷达转接板上，再将激光雷达转接板通过4根10mm长的铜柱和8颗螺钉安装在玻纤底板上。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble10.jpg)

11. **底板铝柱的安装**

现将两段60mm长的铝柱通过双头螺柱串联为120mm长的铝柱，再将8根铝柱通过螺钉固定在玻纤底板上。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble11.jpg)

12. **中层板的安装**
 
使中层板上铝柱通过穿过中层板对应孔位的双头螺柱和底板上铝柱连接，拧紧铝柱，即可将中层板固定在两段铝柱之间。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble12.jpg)

13. **后视激光雷达的安装**

首先将现有的激光雷达安装在激光雷达转接板上，再将激光雷达转接板通过4根10mm长的铜柱和8颗螺钉安装在玻纤中层板上。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble13.jpg)

14. **左右侧门及后侧门上合页的安装**

以左侧门为例，将合页的一片通过两对螺钉、螺母固定在侧缘板上，再将另一片通过两对螺钉、螺母固定在左侧门对应孔位上。（全机共有6个合页）。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble14.jpg)

15. **磁吸铁片的安装**

以左侧门为例，将磁吸铁片通过两对螺钉、螺母固定在侧板的槽孔上（全机共有6个磁吸铁片）。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble15.jpg)

16. **磁吸的安装**

以顶板为例，将磁吸通过两对螺钉、螺母固定在顶板对应的孔上（全机共有6个磁吸）。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble16.jpg)

17. **顶板把手的安装**

将把手通过两个螺钉固定在玻纤底板后侧的孔上。
![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble17.jpg)

18. **法兰的安装**

以顶板为例，将法兰通过三对螺钉、螺母固定在底板上（全机有6个法兰）。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble18.jpg)

19. **侧板的安装**

将各前侧板及侧缘板卡到底板对应的矩形槽孔中即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble19.jpg)

20. **顶板的安装**

将顶板上的矩形槽孔卡入前侧板及侧缘板上的凸台。然后，使M4的螺钉穿过顶板上对应孔位和中板上铝柱连接，拧紧螺钉，即可将顶板固定在螺钉和铝柱之间。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble20.jpg)

21. **铝杆的安装**

将直径19mm的铝杆自上而下依次插入顶层、中层、底层的法兰中，然后拧紧法兰侧边的紧定螺钉即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble21.jpg)

22. **云台板的安装**

先将法兰安装在云台板上，再将云台板通过法兰安装在两根铝杆上（使法兰的紧定螺钉穿过铝杆上的螺纹孔）即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble22.jpg)

23. **Xtion的安装**

先将Xtion的耳片插入3D打印的支撑件内，并扣合盖板，然后将3D打印的扣合件通过两对螺钉、螺母固定在云台的U形架上。然后再将支撑件和扣合件扣合在一起即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble23.jpg)

24. **云台的安装**

将云台底板通过4根40mm铜柱和8颗螺钉连接在一起即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble24.jpg)

24. **磁吸的调整**

若感觉磁吸的效果不好（吸力过大或过小），可调节磁吸铁片的位置。

25. **电源管理的安装**

先将后侧门打开，再将电源管理模块下面的四个橡胶脚垫放在玻纤底板对应的孔上，并轻轻用力压紧即可。

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_assemble25.jpg)

## 附录： 各结构板件安装孔位说明

### 底板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_baseboard.jpg)

### 中板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_middleboard.jpg)

### 顶板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_upperboard.jpg)

### 侧门:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_sideboard.jpg)

### 侧缘板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_ceyuanboard.jpg)

### 后侧板:
![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_backboard.jpg)

### 云台板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_headboard.jpg)

###  激光雷达转接板:

![Alt text](/images/Mechanical/giraffe/wiki/giraffe_small_laserboard.jpg)

