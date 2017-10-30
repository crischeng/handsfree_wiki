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
