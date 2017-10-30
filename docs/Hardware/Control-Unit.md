# HandsFree ControlUnit（V2 & Mini）
-----------------------------
## HandsFree Control Unit V2使用手册

### 目录
- 简介
- 原理图
- 板载资源
- 使用说明
--------------------------------------------
> ### 简介

Hands Free Control Unit V2 是Hands Free Team在第一代主控的基础上改进而来，根据Hands Free开源项目的硬件标准开发的一款的运动控制器，由核心板和底板组和而成，是Hands Free所有平台的重要组成部分，可以应用于轮式机器人，人形机器人，平衡车，旋翼和固定翼的开发。

由于Hands Free建立了一个自己的机械，电路，嵌入式标准，所以Control Unit 还会支持Hands Free Team后续开发的软硬件。你既可以用这款控制器进行自主开发，也可以使用Hands Free嵌入式软件库OpenRE来开发，OpenRE提供了足够多的底层驱动代码和机器人代码库，以及代码的使用手册和测试案例，而且所有源码都是以BSD协议开源的。
关于OpenRE请看： [https://github.com/HANDS-FREE/OpenRE](https://github.com/HANDS-FREE/OpenRE "OPENRE")


> ### 原理图

##### HandsFree ControlUnit V2 PCB正面和背面图
![HANDSFREE_ControUnit_V2_Schematic](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_PCB.jpg)

##### HandsFree ControlUnit V2 原理图part1
![HANDSFREE_ControUnit_V2_Schematic](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part1.png)

##### HandsFree ControlUnit V2 原理图part2
![HandsFree_controlUnit_V2_Sch_part2](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part2.png)

##### HandsFree ControlUnit V2 原理图part3
![HandsFree_controlUnit_V2_Sch_part3](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part3.png)
##### HandsFree ControlUnit V2 原理图part4
![HandsFree_controlUnit_V2_Sch_part4](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part4.png)
##### HandsFree ControlUnit V2 原理图part5
![HandsFree_controlUnit_V2_Sch_part5](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part5.png)

##### HandsFree ControlUnit V2 原理图part6
![HandsFree_controlUnit_V2_Sch_part6](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part6.png)

##### HandsFree ControlUnit V2 原理图part7
![HandsFree_controlUnit_V2_Sch_part7](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part7.png)

##### HandsFree ControlUnit V2 原理图part8
![HandsFree_controlUnit_V2_Sch_part8](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part8.png)

##### HandsFree ControlUnit V2 原理图part9
![HandsFree_controlUnit_V2_Sch_part9](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_Sch_Part9.png)

> ### 板载资源

#### HandsFree ControlUnit V2 正面图
![HANDSFREE_ControUnit_V2_top_view](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_front.jpg)

#### HandsFree ControlUnit V2 背面图
![HANDSFREE_ControUnit_V2_bottom_view](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_V2/HandsFree_ControlUnit_V2_back.jpg)

#### 关键特征
1.	168MHZ  STM32F407  Cortex M4
2.	板载三轴陀螺仪，三轴加速计，气压计，三轴磁力计。
3.	10PWM输入输出。
4.	USBTTL,  USB，microSD卡。
5.	支持机型： 两轮平衡车，两轮差移动平台，三轮全向平台，四轮差速平台，四轮麦克纳姆轮全向平台，数字舵机人形，固定翼，四六八轴旋翼飞行器等。

#### 处理器
1.	32bit STM32F407 VGT6 Cortex M4 core with FPU
2.	168MHZ
3.	192KB SRAM  1M Flash
4.	封装类型：LQFP,   引脚个数：100

#### 板载传感器
1.	MPU6050 6轴运动处理 ， 加速计陀螺仪。
2.	MEAS MS5611高精度气压计。
3.	3-轴数字罗盘IC HMC5883L

#### 板载IC
1.	大容量IIC快速存储器52KB EEPROM
2.	专用ADC基准电压芯片LM4030A，电压采样精度高，可接固定翼用的空速计。
3.	板载5V，3A大电流稳压IC。
4.	集成CP2102 USB串口芯片。
5.	集成VP230 CAN控制芯片。
6.	集成三态门IC，用于数字舵机通信
7.	板载多路电源保护器件，防反接，防过流，抵抗静电，支持多路USB和电源同时供电。
8.	板载SBUS反相器电路，支持遥控器信号读取。

#### 板载接口
1.	四个电机控制以及编码器接口，支持常见类型的机器人平台控制。
2.	10路PWM输出，可同时作为输入，用于搭建多轴飞行器或者舵机控制。
3.	三路串口，USART2  UART4  USART6。
4.	一路USB串口 USART1。
5.	一个USB主从机接口。
6.	一个microSD卡接口。
7.	一路SBUS遥控器采集接口，用于采集航模遥控器的信号。
8.	一路PPM遥控器采集接口，用于采集航模遥控器的信号，PPM接口还可用于扩展空速计。
9.	一路数字舵机控制接口,支持AX12系列的数字舵机。
10.	一个GPS接口，支持外部IIC陀螺仪和磁力计，兼容PX4接口。
11.	一路CAN总线接口，可用于通信组网。
12.	一路IIC接口，可用于扩展外部惯导传感器或者超声波等。
13.	一路SPI接口。
14.	除了以上，板载还有多个led显示，一个蜂鸣器，SWD烧写，复位电路等，电源电压采集电路等。
15.	电源支持7~28V输入。

#### 总结
HANDSFREE控制器，板载资源十分丰富，下料十足，可满足常见形态机器人研究需求，同时不惜成本，尽量选择稳定可靠的接口和IC，光是一个ADC基准电压的芯片就十几块钱，MOLEX接口也是选用昂贵的自锁接口，这主要是因为HANDSFREE团队本身也是使用这款控制器进行研究开发的，所以在很多细节方面考虑也是为了满足自己需求。

同时HANDSFREE团队为该控制器开发了OpenRE嵌入式机器人库，用户可以方便的在此库的基础上进行应用程序构建。而且OpenRE是还可以完全支持在linux环境下开发，这大大方便了ROS开发者和不懂嵌入式的机器人开发者。

> ### 使用说明

HandsFree ControlUnit V2 控制器是在第一代主控基础上发展而来一款多用控制器，不仅仅可以用于控制小车等地面移动平台，也可以用于飞行器的控制，在吸取第一代主控的优点不足的基础上进行改造，设计了自己的核心板，并且将众多传感器集成在核心板上，主控板支持7~12V的电源输入。

[电路板使用教程链接](https://github.com/HANDS-FREE/HANDS-FREE.github.io/wiki/7.-OpenRE-Tutorial)

---------------------------

## HandsFree mini Control Unit 使用手册
### 目录
- 简介
- 原理图
- 使用说明
- 板载资源  
-------------------------

> ### 简介

Hands Free mini Control Unit  是Hands Free Team根据Hands Free开源项目的标准开发的一款的运动控制器，是Hands Free mini移动平台的重要组成部分。Hands Free mini移动平台是Hands free团队专为广大机器人学生爱好者开发的一款助学平台，价格低廉，性价比超高。麻雀虽小五脏俱全，Hands free mini移动平台同样可以用来进行移动导航和视觉开发。而Hands free mini Control Unit则是mini移动平台的核心部分，我们根据mini移动平台的特点将驱动集成在mini控制器上。同时增加了蓝牙模块和集成的MPU6050。

> ### 原理图

#### 图1   HandsFree mini ControlUnit  PCB正面和背面图
![HandsFreeminiControl_function](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_PCB.jpg)

#### 图2 HandsFree mini ControlUnit  原理图part1
![HandsFree_mini_controlUnit_Sch_part1](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Sch_Part1.png)

#### 图3  HandsFree mini ControlUnit  原理图part2
![HandsFree_mini_controlUnit_Sch_part2](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Sch_Part2.png)

#### 图4  HandsFree mini ControlUnit  原理图part3
![HandsFree_mini_controlUnit_Sch_part3](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Sch_Part3.png)

#### 图5  HandsFree mini ControlUnit  原理图part4
![HandsFree_mini_controlUnit_Sch_part4](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Sch_Part4.png)

> ### 使用说明

#### 图6  HandsFree mini ControlUnit 正面图
![HANDSFREE_mini_ControUnit_top_view](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Front.jpg)

#### 图7  HandsFree mini ControlUnit 背面图
![HANDSFREE_mini_ControUnit_bottom_view](/images/Hardware/HandsFree_ControlUnit/HandsFree_ControlUnit_Mini/HandsFree_ControlUnit_Mini_Back.jpg)

HandsFree mini ControlUnit  控制器支持12V电源输入，同时允许转接电源。图6中电源输入口为黄色的xt60接口，同时带有两个12V电源转接口，允许转接到其他设备使用。HandsFree mini ControlUnit  控制器是专为HandsFree mini 移动平台量身打造的一款控制器。其功能齐全性价比超高，配合方便使用的嵌入式代码收到广大学生用户的喜爱。

mini控制板上设置一个电源开关，接通12V电源后按下开关主控器便开始工作，此时电源指示灯会变亮。控制板四周接有4个电机接口，两个串口，一个SPI接口，一个miniusb接口，一个SWD接口，一个can总线接口。同时控制板上集成了两块电机驱动，一块MPU6050，一个蓝牙，极大的方便了用户进行开发。
> ### 板载资源

- STM32F103芯片
- mpu6050加速计陀螺仪
- 4路电机控制接口：支持hands free team 开发的电机驱动，可用于搭载hands free 3wd轮式机器人或者hands free 2轮平衡车，hands free mini移动平台。
- 1路can总线：板载1个can接口，可用于通信，或者扩展hands free imu 高精度单轴陀螺仪
- 1路spi接口
- 1路双座USB母座接口：提供转接5V电源
- 2路串口接口： usart4  uart5
- 一个usb串口：采用ft232 usb 串口芯片  usart4，可usb线升级固件和通信
- 1个swd程序烧写接口
- 1个蓝牙

> ### 使用说明

#### 电路板使用方式与V2一致
