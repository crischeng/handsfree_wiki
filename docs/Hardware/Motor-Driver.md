## HandsFree Motor Drive V2使用手册
### 目录
- 简介
- 原理图 
- 使用说明
------------------------------------
> ### 简介

HandsFree Motor Drive V2 是HandsFree Team根据Hands Free开源项目的标准开发的一款电机驱动器，是HandsFree开发的机器人Stone的硬件的组成部分之一。每块驱动板使用两块BTS7970芯片，可以驱动一个电机，保证足够大的驱动能力。同时能够将电源转接给其他驱动，极大的减少驱动电源线连接的复杂程度。第二代电机驱动板是在HandsFree_ Motor_ Driver_V1版本上优化而来，在保留了第一代版本的特点的同时新加了电流采样电路，因此不仅能够接收到更多的来控制电机，同时使得对电机的软保护成为了可能，有效的防止电机的堵转。另外还增加了防反接功能，杜绝了在错误连接时对驱动烧坏的可能。

> ### 原理图

##### 图1&nbsp;&nbsp;&nbsp;&nbsp;HandsFree _ Motor _ Driver _ V2 _ sch _ part1
![HandsFree_Motor_Driver_V2_sch_part1](/images/Hardware/HandsFree_Motor_Drive/HandsFree_Motor_Drive_V2/HandsFree_Motor_Driver_V2_Sch_Part1.jpg)

##### 图2&nbsp;&nbsp;&nbsp;&nbsp;HandsFree _ Motor _ Driver _ V2 _ sch _ part2
![HandsFree_Motor_Driver_V2_sch_part2](/images/Hardware/HandsFree_Motor_Drive/HandsFree_Motor_Drive_V2/HandsFree_Motor_Driver_V2_Sch_Part2.jpg)
##### 图3&nbsp;&nbsp;&nbsp;&nbsp;HandsFree _ Motor _ Driver _ V2 _ sch _ part3
![HandsFree_Motor_Driver_V2_sch_part3](/images/Hardware/HandsFree_Motor_Drive/HandsFree_Motor_Drive_V2/HandsFree_Motor_Driver_V2_Sch_Part3.jpg)

##### 图4&nbsp;&nbsp;&nbsp;&nbsp;HandsFree _ Motor _ Driver _ V2 _ sch _ part4
![HandsFree_Motor_Driver_V2_sch_part4](/images/Hardware/HandsFree_Motor_Drive/HandsFree_Motor_Drive_V2/HandsFree_Motor_Driver_V2_Sch_Part4.jpg)


> ### 使用说明

##### 图5&nbsp;&nbsp;&nbsp;&nbsp;HANDS _ FREE _ Driver _ V2 _ function

![HANDSFREE_Driver_V2_function](/images/Hardware/HandsFree_Motor_Drive/HandsFree_Motor_Drive_V2/HandsFree_Motor_Driver_Function.png)

#### 细节描述
- 驱动芯片：BTS7970
- 铜柱间距：	1220mil × 1690mil (40mil = 1mm)  3MM铜柱
- 板子大小：	1400mil × 1900mil
- 电流采样：0.34V/A	 Max:<6A(瞬态) 建议软启动下使用。
- 输入电源大小：5~35V， 防反接保护。
- 输入接口：	[电源输入接口][扩展电源接口][HANDSFREE标准电机接口]
- 输出接口：
  <主方案>	[电机接口] xh2.54mm 6P
  <自定义方案>	VCC5.0 GND 编码器AB相 焊盘*4 电机+ 电机焊盘

- 状态显示：[电机正反转 LED显示]	[输入电源 LED显示][信号电源LED显示]

*对于使用HANDSFREE接口电机的用户只需要把电机接上，控制接口连到主控就行，对于使用其他电机的用户，可以把电机和编码器的线焊接到驱动板的背面。*

#### 注意
BTS支持大功率电机驱动，但是由于电流采样电路只支持6A以内，所以若是使用大功率电机，可以通过去掉电流采样电路并加上金属散热片来实现，具体方法就是去掉R050这个0.5r的电阻，并把焊盘两端短路，同时去掉电解电容，在BTS上贴一个金属散热片。注意：如不进行此操作，直接驱动大功率电机可能会烧掉电流采样电阻。
