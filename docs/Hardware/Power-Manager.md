## HandsFree Power Manager V2使用手册


### 目录
- #### 简介

- #### 供电方案

- #### 原理图

- #### 接口说明

--------------------------------------------

> ### 简介
&nbsp;&nbsp;&nbsp;Hands Free Power Manager V2.0 是 Hands Free Team 根据 Hands Free 开源项目的硬件标准设计的一款电源分配板，附带多路开关和多种电源转换功能，满足机器人多样的电力需求。 支持常用的 TX1， TK1， MiniPC，树莓派， Kinect ，HOKUYOU 雷达等设备供电，同时还支持机器人的电机驱动， 云台舵机，机械臂等结构的供电，还自带一个急停开关接口和 1 一路急停电源输出。 配合大容量电池可以为机器提供集成供电方案。

> ### 供电方案
&nbsp;&nbsp;&nbsp;HandsFree 在中型及以上的移动平台上采用集成化的供电方案，这是为了简化机器人开发者对电源的设计同时方便开发者进行多种形式的开发。在电源板上有数量众多的电源接口，提供多种不同的电压，可以给各种形式的设备进行供电。同时我们定义了不同接口的所代表的不同电压，保证了不同的电压的设备和接口不能顺利连接在一起，从而保护设备。
![HandsFree_Power_Scheme](/images/Hardware/HandsFree_Power_Manager/HandsFree_Power_Manager_V2/PowerSupply.png)
<p align="center">图1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HandsFree 集成供电方案</p>

> ### 原理图
&nbsp;&nbsp;&nbsp;为了满足开发者不同设备的所需的不同电压，我们将输入电压变压成12V、5V、19V，并提供足够大的驱动能力。12V输出部分最大可以有3A电流输出，5V电压部分最大可以有3A电流输出，19V电压部分最大可以有3A电流输出。我们定义了机器人驱动轮的电机电压为电池的输入电压。在HandsFree Power Manager V2电源管理板上允许输入的电压有12V和24V，这意味着可以去驱动12V和24V的电机，但是输入不同的电压需要做一些不同的处理。在输入12V电压时需要将板子中的12V/24V保险丝焊接起来（将24V转12V模块短路），同时需要把19V模块接成12V转19V模块。这样输出的电源电压为12V。在电池输入为24V时，12V/24V保险丝不需要焊接，同时19V模块接为24V转19V。
![HandsFree_Power_manager_V2_sch_part1](/images/Hardware/HandsFree_Power_Manager/HandsFree_Power_Manager_V2/Power_Manager_Sch_Part1.png)

<p align="center">图2
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HandsFree Power Manager V2 sch part 1 </p>

![HandsFree_Power_manager_V2_sch_part2](/images/Hardware/HandsFree_Power_Manager/HandsFree_Power_Manager_V2/Power_Manager_Sch_Part2.png)

<p align="center">
图3
&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;
HandsFree Power Manager V2 sch prat 2
</p>

![HandsFree_Power_manager_V2_sch_part3](/images/Hardware/HandsFree_Power_Manager/HandsFree_Power_Manager_V2/Power_Manager_Sch_Part3.png)

<p align="center">
图4
&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;
HandsFree Power Manager V2 sch prat 3
</p>

> ### 接口说明
&nbsp;&nbsp;&nbsp;&nbsp;电机接口和电源接口输出电压为电池电压，可以为12V或者24V，采用接口5557弯针插座。主控接口和12V电压输出的接口采用MX3.0mm间距2P连接器都是12V电压输出，主控的电压输出可以由主控开关控制。19V电压接口采用MX3.0mm间距2×2P连接器。19V电压输出由19V开关控制。5V的电压输出有两种接口，一种是5VUSB接口，另一种是5V舵机接口。5V的舵机接口采用XH2.54-3P 间距2.54MM 弯针插座。具体的接口位置在图5中可以看到。

![HandsFree_Power_Manager_V2_Function_view](/images/Hardware/HandsFree_Power_Manager/HandsFree_Power_Manager_V2/Power_Manager_interface_introduction.png)
<p align="center">
图5
&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;HandsFree Power Manager V2 接口说明
</p>
