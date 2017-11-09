# HandsFree与Turtlebot对比

## 参数汇总

| 类型  	        | Mini          | Stone |Giraffe |Turtlebot2 |Burger |Waffle    |
| ------------- |:-------------:| -----:|-------:|----------:|------:|---------:|
| 高度(cm)       | 20.4/33.3     | 33.2/125.2 | 33.2/126.2| 12.48 | 19.2 | 14.1 |
| 重量(kg)       | <2            |   约3 | <12 | 5| 1 | 1.8 |
| 直径(cm)       | 23     | 36     |   38 | 35.15 | 14,18 | 28,30.6 |
| 最大速度(m/s)   |   1.2   | 1.2    | 1.6   | 0.7   | 0.22   | 0.26  |
| 额定承载能力(kg) |    6   |  15   | 40   |  5  |  15  | 30  |
| 主控板类型      |   STM32F1基础上开发的HandsFree mini ControlUnit    |  STM32F4基础上开发的HandsFree Control Unit V2   | STM32F4基础上开发的HandsFree Control Unit V2   |  未知  |  STM32F7基础上的Arduino开发板 | STM32F7基础上的Arduino开发板 |
| 电源接口        |  12V5V19V(max均 3A)     |  12V5V19V(max均 3A)   |  12V5V19V(max均 3A)  | 19V/2A 12V/5A 12V/1.5A 5V/1A   | 3.3V/0.8A 5V/4A 12V/1A   | 3.3V/0.8A 5V/4A 12V/1A  |
| 支持外接设备     |   TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等     |  TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等    | TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等    | 请参考上述接口   |  请参考上述接口  | 请参考上述接口  |
| 电源容量(mAh)   |   7800    |  7800   |  7800  | 2200/4400   |  1800  | 1800 |
| ROS雷达导航开发  |   支持    |  支持   | 支持   | 支持   | 支持   | 支持   |
| ROS视觉导航开发  |   支持    |   支持  | 支持   | 支持   |  未知  | 未知  |
| 下位机软件      |    OpenRE   |   OpenRE  | OpenRE   |  未知  |  OpenCR  | OpenCR  |
| 价格(RMB)      |   1899/4499/6699  |  3399/5799/8699  | 9999   |  11399  | 5500  |  15500 |

说明:

* Turtlebot2除价格外其他参数均为Kobuki移动底盘的参数.
* 高度一栏格式为:不加云台高度/加云台之后高度
* 价格一栏格式为:基础版/导航版/视觉开发版
* Turtlebot3系列直径为:长,宽

---

本文档为HandsFree机器人与Turtlebot公司机器人的对比报告,.报告内容将从**硬件**,**软件**,**售后**三个方面来进行对比.

# 一,概述

## 1.1 HandsFree

 > HandsFree 是一个面向机器人研究、开发的开源软硬件系统。她有完备与科学的框架,以优秀的嵌入式系统框架为核心,精良的电路、机械设计为支撑,帮您快速实现多种形态的机器人。本系统包含机器人导航,SLAM,计算机视觉等模块,并拥有自己上层软件和调试系统。她支持国外其他的开源项目,如 ROS, MPRT, PIXHAWK 等,这一切都为您带来了无比的便捷和快乐!    
 
 HandsFree现在主推三款机器人分别是Mini,Stone,Giraffe,分别面向不同需求.简介如下:    
1,[Mini](http://wiki.handsfree.org.cn/docs/Products/Mini.html)是一款采用前万向后双驱动轮底盘布局的小型机器人。其整机结构采用平板桁架式透明化设计，外形简约大方，能支持多种激光雷达，TK1、树莓派等主流控制器，可搭载assustion、Kinect1 、Kinect2等深度摄像头。Mini体型小、功能强大、性价比高，非常适合入门者开发研究和多机集群应用研究。效果如图:

![Mini](/images/Products/m_2.jpg)


2,[Stone](http://wiki.handsfree.org.cn/docs/Products/Stone.html)是一款采用前万向后双驱动轮底盘布局的智能车平台。其整机结构采用平板桁架式透明化设计，外形简单又不失机械美感。Stone可搭载Dobot1、Dobot m1等小型机械臂，能支持多种激光雷达，TX1、TK1、树莓派等主流控制器。其配备高度可调的两轴云台，兼容多款RGBD摄像头和单、双目摄像头。效果如图: 

![Stone](/images/Products/s_2.jpg)

3,[Giraffe](http://wiki.handsfree.org.cn/docs/Products/Giraffe.html)是一款采用前万向后双驱动轮底盘布局的智能车平台。其整机结构采用平板桁架式封闭式设计；侧板采用带磁吸可开合设计；传动系统采用同步带传动。Giraffe可同时支持一前一后两个激光雷达，兼容TX1、TK1、树莓派等主流控制器，配备高度可调、能兼容多款RGBD摄像头和单、双目摄像头的两轴云台。Giraffe可搭载HF Arm1等中型机械臂（总量15Kg左右），具有高达40Kg的承载能力。效果如图:

![Giraffe](/images/Products/g_1.jpg)

## 1.2 Turtlebot

英文是介绍的原文,中文下面中文进行了简要的翻译   
> TurtleBot is a low-cost, personal robot kit with open-source software. TurtleBot was created at Willow Garage by Melonee Wise and Tully Foote in November 2010. With TurtleBot, you’ll be able to build a robot that can drive around your house, see in 3D, and have enough horsepower to create exciting applications.   
> The TurtleBot kit consists of a mobile base, 2D/3D distance sensor, laptop computer or SBC(Single Board Computer), and the TurtleBot mounting hardware kit. In addition to the TurtleBot kit, users can download the TurtleBot SDK from the ROS wiki. TurtleBot is designed to be easy to buy, build, and assemble, using off the shelf consumer products and parts that easily can be created from standard materials. As an entry level mobile robotics platform, TurtleBot has many of the same capabilities of the company’s larger robotics platforms, like PR2.    
> Turtlebot是一种低成本，具有开源开源软件的个人机器人开发套件。利用Turtlebot，你将能够建立一个可以驱动你的房子周围的机器人，看3D视图，并有足够的马力，并创造令人兴奋的应用。   
> Turtlebot开发套件由一个移动底盘，二维/三维距离传感器、笔记本电脑或SBC（单板计算机），和turtlebot安装硬件套件组成。还有,对turtlebot套件来说，用户可以从ROS的wiki上下载Turtlebot SDK。Turtlebot设计易于购买，建造，安装，使用现成的消费产品和零件，很容易可以从标准的材料制造。作为一款入门级的移动机器人平台，Turtlebot有许多的公司更大的机器人平台相同的功能，比如PR2机器人。   

下面简要介绍一下机器人,Turtlebot现存的机器人有第二代和第三代的机器人,这两代机器人差别比较大.   
1,[Turtlebot2](http://www.turtlebot.com/turtlebot2/)是一个系列,大部分都是由Kobuki移动底盘,华硕的Xtion深度摄像头/kinect深度摄像头,一个可以上网的笔记本,还有放置笔记本和kinect的各种结构,机器人.机器人主要的部分就是kobuki移动底盘,摄像头和可联网的PC.但是第二代机器人的移动底盘是封装好了的,内部机械及软件均是不开源的,只留下了更新固件接口及其他一些接口.因为不开源我们无法对其进行更多的分析,但不可否认的是,这个移动底盘确实比较稳定和准确.效果如图:
![Turtlebot2](/images/Products/turtlebot2.png)
2,[Turtlebot3](http://turtlebot3.robotis.com/en/latest/)也是一个系列,现在主要的两款是Burger和Waffle.主要由树莓派,一块Arduino板,还有雷达组成.有人尝试在上面加装深度摄像头和机械臂,但是感觉也只是装饰,由于高度的限制,只有雷达能够发挥出全部的作用.第三代机器人和第二代机器人来比较的话,变化非常大.(1)更加地低成本,选取的硬件都很low,有点面向高中生的意思,在上面计算怕是不行.(2),全部开源,第三代机器人的硬件软件全部是开源的,不像第二代,移动底盘是一个集成好了的产品.效果如图:

![Turtlebot3](/images/Products/turtlebot3.png)


# 二,硬件对比

因为Turtlebot2并不是全部开源,所以我们在对比的时候会将所知的Turtlebot2的信息提及,但是主要将对Turtlebot3和HandsFree举例进行比较.

## 2.1  机械

### 2.1.1 参数差异

机械方面,HandsFree有三款机器人,小型的Mini到大机器人Giraffe,不同规格满足不同需求.Turtlebot方面第二代产品与我们的中型产品Stone大小类似,第三代产品与Mini类似.由于Turtlebot2的核心是kobuki移动底盘,我们将主要介绍kobuki的参数,下面是对比:

| 类型  	        | Mini          | Stone |Giraffe |Kobuki  |Burger |Waffle    |
| ------------- |:-------------:| -----:|-------:|----------:|------:|---------:|
| 高度(cm)       | 20.4/33.3     | 33.2/125.2 | 33.2/126.2| 12.48 | 19.2 | 14.1 |
| 重量(kg)       | <2            |   约3 | <12 | 5| 1 | 1.8 |
| 直径(cm)       | 23     | 36     |   38 | 35.15 | 14,18 | 28,30.6 |
| 最大速度(m/s)   |   1.2   | 1.2    | 1.6   | 0.7   | 0.22   | 0.26  |
| 额定承载能力(kg) |    6   |  15   | 40   |  5  |  15  | 30  |

说明,高度一栏中HandsFree机器人的两个高度分别为加云台和不加云台,Turtlebot3系列直径为长乘宽.

### 2.1.2 说明分析

机械结构来说,HandsFree占据更多优势.   

* 高度,要知道,所有的深度摄像头都有一个盲区,比如说Xtion2的有效距离是0.8~3.5m,但是Turtlebot3高度太低,会有很大的盲区.HandsFree每款机器人都有架高了的云台,视野更好.    
* 速度,由于较好的稳定性,HandsFree的速度都要比Turtlebot要快   
* 承载能力方面,相差不是特别大,而且如果是加装机械臂的话,感觉Turtlebot3底盘实在是太低了.Handsfree其中两款都可以加装机械臂,位置也比较合适.   
* 云台,Turtlebot所有系列都没有云台,而HandsFree所有的机器人都可以加装云台,可以使视野更广.

## 2.2 主控制器

### 2.2.1 参数介绍 

HandsFree中Mini用的控制器是[HandsFree mini ControlUnit](http://wiki.handsfree.org.cn/docs/Hardware/Control-Unit.html),另外两款使用的是[HandsFree Control Unit V2](http://wiki.handsfree.org.cn/docs/Hardware/Control-Unit.html),这两款软硬件全部开源.Turtlebot2底盘控制是个黑箱子,既不能自己拓展应用又不能自主开发,很赚钱,毕竟人家是专业的靠这个吃饭的,做出来的控制效果和里程计的精确度可能会比较高,但是没有参数,我们并不能进行比较,但是Turtlebot3是全部开源的,我们可以拿来比较一下(其实我都不想比,简直可笑...).   
HandsFree Control Unit V2,主要特征:   

* 168MHZ STM32F407 Cortex M4   
* 板载三轴陀螺仪，三轴加速计，气压计，三轴磁力计。   
* 10PWM输入输出。   
* USBTTL, USB，microSD卡。   
* 支持机型： 两轮平衡车，两轮差移动平台，三轮全向平台，四轮差速平台，四轮麦克纳姆轮全向平台，数字舵机人形，固定翼，四六八轴旋翼飞行器等。   

细节看下图,可以在[链接](http://wiki.handsfree.org.cn/docs/Hardware/Control-Unit.html)中查看更多细节.  

![Control Unit 参数](/images/Products/handsfree.jpg)

Turtlebot3使用的是基于STM32F7开发的Arduino开发板,MCU不错,板子上其他的东西不多:

![Turtlebot3 参数](/images/Products/turtlebot3canshu.jpg)

我顺便把Mini的参数放上去吧:

![Mini 参数](/images/Products/mini.jpg)

### 2.2.2 说明分析

* Turtlebot2的底盘控制器可能比我们的要好,已知的只有防撞传感器,红外传感器,防跌落传感器,110度/s单轴陀螺仪.   
* HANDSFREE控制器，板载资源十分丰富，下料十足，可满足常见形态机器人研究需求，同时不惜成本，尽量选择稳定可靠的接口和IC，光是一个ADC基准电压的芯片就十几块钱，MOLEX接口也是选用昂贵的自锁接口，这主要是因为HANDSFREE团队本身也是使用这款控制器进行研究开发的，所以在很多细节方面考虑也是为了满足自己需求。   
同时HANDSFREE团队为该控制器开发了OpenRE嵌入式机器人库，用户可以方便的在此库的基础上进行应用程序构建。而且OpenRE是还可以完全支持在linux环境下开发，这大大方便了ROS开发者和不懂嵌入式的机器人开发者。   
* Turtlebot3的MCU比较高端,但是开发板上的资源倒是有限,感觉有点浪费了.   

**总结**:Turtlebot3板载资源只能跟Mini稍微比较一下,和HandsFree第二代上的板载资源完全没有比较性.Kobuki底盘控制器参数未知,程序也不是开源的,无法进行比较,只能说可能有一定优势.

## 2.3 电源供电方案

### 2.3.1 参数介绍

[Hands Free Power Manager V2.0](http://wiki.handsfree.org.cn/docs/Hardware/Power-Manager.html) 是 Hands Free Team 根据 Hands Free 开源项目的硬件标准设计的一款电源分配板，附带多路开关和多种电源转换功能，满足机器人多样的电力需求。 支持常用的 TX1， TK1， MiniPC，树莓派， Kinect ，HOKUYOU 雷达等设备供电，同时还支持机器人的电机驱动， 云台舵机，机械臂等结构的供电，还自带一个急停开关接口和一路急停电源输出。 配合大容量电池可以为机器提供集成供电方案。

![Power](/images/Products/Power.png)

Turtlebot2移动底盘有对外的接口,内置电池,Turtlebot3也设置了对外接口.   
下面是二者的对比:   

| 类型  	        | Mini          | Stone |Giraffe |Turtlebot2 |Burger |Waffle    |
| ------------- |:-------------:| -----:|-------:|----------:|------:|---------:|
| 电源接口        |  12V5V19V(max均 3A)     |  12V5V19V(max均 3A)   |  12V5V19V(max均 3A)  | 19V/2A 12V/5A 12V/1.5A 5V/1A   | 3.3V/0.8A 5V/4A 12V/1A   | 3.3V/0.8A 5V/4A 12V/1A  |
| 支持外接设备     |   TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等     |  TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等    | TX1,TK1,MiniPC,树莓派,Kinect ,HOKUYOU 雷达等    | 请参考上述接口   |  请参考上述接口  | 请参考上述接口  |
| 电源容量(mAh)   |   7800    |  7800   |  7800  | 2200/4400   |  1800  | 1800 |

### 2.3.2 说明分析

无论是在电池容量和接口方面,HandsFree都相对更加优秀.HandsFree提供了专门的电源模块,支持的可搭载模块更多.

## 2.4 电机,驱动

* [HandsFree Motor Drive V2](http://wiki.handsfree.org.cn/docs/Hardware/Motor-Driver.html) 是HandsFree Team根据Hands Free开源项目的标准开发的一款电机驱动器，是HandsFree开发的机器人Stone的硬件的组成部分之一。每块驱动板使用两块BTS7970芯片，可以驱动一个电机，保证足够大的驱动能力。同时能够将电源转接给其他驱动，极大的减少驱动电源线连接的复杂程度。   
* Turtlebot2驱动电机均未知.Turtlebot3使用[Dynamixel X series](http://en.robotis.com/index/product.php?cate_code=10121110);Burger电机为DYNAMIXEL (XL430-W250-T),Waffle电机为DYNAMIXEL (XM430-W210-T).   

感觉这方面半斤八两吧.

# 三,软件对比

软件方面将从上位机软件(ROS)和下位机软件(OpenRE/OpenCR)分别介绍.

## 3.1 ROS

[ROS](http://wiki.ros.org/)(Robot Operating System)是一个开源的平台,也是一个提供各种库文件帮助软件开发人员创建机器人应用程序的工具。它提供了硬件抽象层、设备驱动程序、库、可视化工具、消息传递、包管理，还有更多其他的。   
Turtlebot和HandsFree上层都是基于ROS进行开发,由于ROS的开源的性质,在上位机软件方面两类机器人差别不大,都可以使用ROS库进行开发,Turtlebot的Demo和HandsFree的Demo都是大同小异,互通有无的.   
所以,在这方面,二者没区别.   

## 3.2 下位机软件

Turtlebot2不是开源的,所以没有第二代的资料,也就是说第二代底层是不支持二次开发的.   
Turtlebot3下位机软件为[OpenCR](http://turtlebot3.robotis.com/en/latest/opencr_software.html#),开发工具为Arduino的IDE. 具体代码没有研读,不过考虑到主控板上资源较少,就算进行二次开发也很受限制.   
HandsFree下位机软件为[OpenRE](http://wiki.handsfree.org.cn/docs/OpenRE/Home.html).
OpenRE全称Open Source Robot Embedded Library，是一个专门为机器人写的、基于STM32系列微处理器的嵌入式开源库。经过不断优化，开源库变得鲁棒和通用，从而独立于平台成为一个专门为机器人而生的一个嵌入式库。主要目的是搭建一个专门为机器人服务的嵌入式跨平台软件框架，涵盖底层设备驱动，算法库，通信与操作系统组件等，主要涵盖以下内容：

* 封装了许多传感器、存储器、输入输出设备的驱动包，并且采用硬件和驱动包隔离的方式，开发者可以轻易的跨平台移植，比如各种伺服设备、数模舵机、直流三相电机、各种传感器、加速计，陀螺仪、磁力计、超声、 GPS、一些交类互 LCD、触摸屏、 flash、 EEPROM、 SD 卡驱动等。
* 具有已经移植好的操作系统层功能，实时操作系统（ RTOS），图形库（GUI），网络协议（LWIP）， USB 协议，使用者可以根据自己的需求，选择合适的模板进行开发，省去了移植过程的繁琐操作。
* 具有很多机器人有关的算法库、 PID 控制包、机器人运动坐标变换包、卡尔曼滤波包、矩阵运算包、四元数等。
* 支持Linux环境下的makefile + QTCreator + armgcc来进行开发

 **总结**:Turtlebot2下位机软件可能会存在算法上的优势,但是不能进行二次开发,第三代开发受限制很多,总体来说不如HandsFree的开源的下位机软件.
 
# 四,销售及服务对比

## 4.1 价格

价格方面也是碾压趋势,HandsFree三款机器人分别对应不同群体,价格区间在2000-10000不止,套餐选择很人性化.Turtlebot系列,第三代价格在6500左右,第二代只要移动底盘就4500,更不要说上面要架设kinect和联网笔记本了.

| 类型  	        | Mini          | Stone |Giraffe |Turtlebot2 |Burger |Waffle    |
| ------------- |:-------------:| -----:|-------:|----------:|------:|---------:|
| 价格(RMB)      |   1899/4499/6699  |  3399/5799/8699  | 9999   |  11399  | 5500  |  15500 |

说明: 价格一栏格式为:基础版/导航版/视觉开发版

## 4.2 Wiki

因为两家机器人都是基于ROS,国内也有在推广ROS的各种组织,所以关于ROS方面的资料都可以找到.TurtleBot系列和HandsFree系列都提供较为完整的学习指导和培训，在GitHub上提供开源的代码供客户学习使用，有自己的讨论社区为广大机器人爱好者提供讨论分享，碰撞思维的平台。   
* Turtlebot系列的其他资料都以Wiki的形式给出,大部分资料都可以在[官网](http://www.turtlebot.com/)找到.
* HandsFree的资料也是依靠gitbook整理形成的[Wiki](http://wiki.handsfree.org.cn/),所有资料都可以在里面找到.不仅如此我们还建有HandsFree社区,社区交流群: 521037187 (Hands Free Community) ,群内大部分都是HandsFree使用者及开发者,大家可以互相学习解惑.
  
## 4.3 Others

HandsFree相对Turtlebot有天然的优势,一堵无形的墙.我们产品如果有什么问题,社区提问,或者直接找到我们公司都不是事.

* 有二十多所大学的实验室,使用了HandsFree平台作为研发平台   
* 十几个创业公司使用了HandsFree作为原型机   
* 软件框架更是被众多机器人爱好者所使用,社区论坛每天都有上千次的浏览量   

HandsFree　搭建了自己的网站,交流社区,淘宝店,Github等,希望能帮助更多机器人开发者.

# 五,综述

* 硬件方面,由于Turtlebot2的不开放我们无法进行比较,但是通过与Turtlebot3的对比,我们发现资本主义都是纸老虎.不能说全面碾压Turtlebot3,但是可以说占据很大的优势了.   
* 软件方面,同是支持ROS开发的机器人,ROS的驱动算法一类的又都是开源的,这方面差别不大,但是Handsfree仍然占据了高地,HandsFree的OpenRE代码解析详细,支持的编译工具更多,支持Linux环境下的makefile + QTCreator + armgcc来进行开发,更地满足了程序员的需求.   
* 销售方面,我们搭配的套餐更加人性化,质量高,价钱低.服务与Turtlebot不相上下,我们还提供了大家互相交流的社区,以及及时方便的售后.   

综上所述,HandsFree是进行机器人开发学习相对更好的选择.

