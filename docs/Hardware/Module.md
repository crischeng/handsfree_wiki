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

## HandsFree Remote 使用手册
> ### 简介

Hands Free Remote V2 是Hands Free Team根据Hands Free开源项目的硬件标准开发的一款遥控器，是Hands Free所有平台的组成部分，可以应用于轮式机器人，人形机器人，平衡车，旋翼和固定翼的开发。

由于Hands Free建立了一个自己的机械，电路，嵌入式标准，所以Remote 还会支持Hands Free Team后续开发的软硬件。你既可以用这款遥控器进行自主开发，也可以使用Hands Free嵌入式软件库OpenRE来开发，OpenRE提供了足够多的底层驱动代码和机器人代码库，以及代码的使用手册和测试案例，而且所有源码都是以BSD协议开源的。

关于OpenRE请看： [OpenRE](https://github.com/HANDS-FREE/OpenRE)

> ### 实物图

#### 图1    Remote正面
![HandsFree_Remote_V2_Picture_top_view](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_Picture_top_view.jpg)   
     
#### 图2    Remote背面  
![HandsFree_Remote_V2_Picture_buttom_view](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_Picture_buttom_view.jpg) 

> ### 电路图

#### 图3    Remote电路图1 
![HandsFree_Remote_V2_sch_part1](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_sch_part1.jpg)    


#### 图4    Remote电路图2  
![HandsFree_Remote_V2_sch_part2](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_sch_part2.jpg)    
 
#### 图5    Remote电路图3 
![HandsFree_Remote_V2_sch_part2](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_sch_part3.jpg)  
 
#### 图6    Remote电路图4 
![HandsFree_Remote_V2_sch_part2](/images/Hardware/HandsFree_Remote/HandsFree_Remote_V2_sch_part4.jpg)   

 
> ### 板载资源
* 关键资源：                     

  1、144MHZ STM32F103 Cortex M3  
  2、板载三轴陀螺仪，三轴加速度计  
  3、USBTTL  
  4、蓝牙4.0

* 处理器：

  1、32bit STM32F103 RCT6 Cortex M3 core with FPU   
  2、144 MHZ    
  3、48KB SRAM 256KB Flash    
  4、封装类型：LQFP， 引脚个数：64
  
* 板载传感器：
 
  1、MPU6050 6轴运动处理，加速度计陀螺仪   
  2、两个双通道摇杆，一个滑动变阻器 
  3、0.96寸OLED

* 板载接口：

  1、一路串口，USART2    
  2、一路USB串口，UART4    
  3、两个双通道摇杆，一个滑动变阻器   
  4、蓝牙4.0   
  5、除了以上，板载还有多个led显示，六个按键，一个蜂鸣器，SWD烧写，复位电路等，电源电压采集电路等   
  6、电源支持2.5-5.5V输入  

## HandsFree Bluetooth_USART

> ### 简介

Hands Free Bluetooth_USART 是HandsFree Team根据Hands Free开源项目的硬件标准开发的一个串口转蓝牙模块。      
由于HandsFree建立了一个自己的机械，电路，嵌入式标准，所以Bluetooth_USART还会支持HandsFree Team后续开发的软硬件。   

> ### 封装图

![HandsFree Bluetooth_USART](/images/Hardware/HandsFree_Module/HandsFree_Bluetooth_USART/HandsFree_Bluetooth_USART_Pcb.jpg)

> ### 板载资源

- 蓝牙4.0芯片
- led
- 3.3V稳压芯片
- 5针串口接口

----------------------

## HandsFree SWD

> ### 简介

Hands Free SWD 是Hands Free Team根据Hands Free开源项目的硬件标准开发的一个SWD转换模块。      
 
> ### 实物图

#### 图1       SWD正面
![HandsFree_SWD_V1_Picture_top_view](/images/Hardware/HandsFree_Module/HandsFree_SWD/HandsFree_SWD_V1_Picture_top_view.jpg)

#### 图2       SWD背面
![HandsFree_SWD_V1_Picture_bottom_view](/images/Hardware/HandsFree_Module/HandsFree_SWD/HandsFree_SWD_V1_Picture_bottom_view.jpg) 

--------------------------

## Hands Free USBTTL

> ### 简介：

Hands Free USBTTL 是Hands Free Team根据Hands Free开源项目的硬件标准开发的一个USB转串口模块。      
由于Hands Free建立了一个自己的机械，电路，嵌入式标准，所以USBTTL还会支持Hands Free Team后续开发的软硬件。    

> ### 实物图：

#### 图1       USBTTL正面
![HandsFree_USB_TTL_V1_Picture_top_view ](/images/Hardware/HandsFree_Module/HandsFree_USB_TTL/HandsFree_USB_TTL_V1_Picture_top_view.jpg)

#### 图2       USBTTL背面
![HandsFree_USB_TTL_V1_Picture_bottom_view](/images/Hardware/HandsFree_Module/HandsFree_USB_TTL/HandsFree_USB_TTL_V1_Picture_bottom_view.jpg) 

> ### 电路图

#### 图3       USBTTL电路图

![HandsFree_USB_TTL_V1_sch](/images/Hardware/HandsFree_Module/HandsFree_USB_TTL/HandsFree_USB_TTL_V1_sch.jpg) 


> ### 板载资源：
- FT232RL芯片    
- 三个LED    
- USB micro接口  
- 5针串口    
