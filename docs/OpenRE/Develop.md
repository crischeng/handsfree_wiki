## 第五章 OpenRE实战
### 代码框架介绍
**OpenRE框架图**
![picture1](/images/OpenRE/Embedded_Architectural.jpg)

OpenRE的代码由底层到上层主要分为**底层接口函数库**、**常用外设驱动库**、**OS库**、**机器人对象的抽象库**、**第三方库的移植**等。  
下面对每每类函数库做简单介绍。
* 底层接口函数库
      在官方固件库的基础上，将对GPIO、定时器、编码器、USART、CAN、IIC、SPI、ADC和PWM等底层资源的操作进一步进行封装。
* 常用外设驱动库
      根据官方固件库，对常用的外设提供驱动，例如电机控制、舵机控制、LCD屏幕驱动、GPS模块解码、航模遥控器的解码和IMU的数据处理等。
* OS库  
      开发的应用程序包含裸跑程序版本和有操作系统版本，该库包含ucos操作系统的相关文件。
* 机器人对象的抽象库  
      对移动底盘模型的抽象，包括差分底盘、4轮麦轮底盘和3轮全向轮底盘等。
* 第三方库的移植
      移植的第三方库，包括Dobot机械臂库，Eigen3和Matrix矩阵库。    
      
### 第三方主控的移植
OpenRE是一个开源机器人嵌入式系统。为了让更多的机器人爱好者能够使用到它，我们在这里推出将OpenRE移植到第三方主控（非HANDSFREE出品主控）的教程。

很多机器人爱好者在接触到OpenRE的时候会有这样的疑问，我有自己的机器人，我有自己的嵌入式主控，可是我想用OpenRE进行开发，我该怎么办呢？关于这个问题，首先，我们要将OpenRE移植到你自己的主控上去，当一切调试顺利之后，参照教程 *4.3基于OpenRE和HandsFree主控编写机器人程序* ，即可让OpenRE运行在自己的机器人上。

接下来，我们就开始第三方主控移植之旅。

在代码框架介绍一节里，大家应该已经掌握到，OpenRE代码按照文件夹的编排可以分为四部分：工程文件、主控描述文件、功能包文件、操作系统文件和第三方库文件。

* 操作系统文件是服务于Ucos操作系统的。
* 第三方库文件是我们在工程中实现某些特定功能时调用的别人已经写好的库.

我们可以暂时将这两份文件放在一边。剩下的三个文件中，
* 主控描述文件是最底层的，它包含了所有与电路板最底层操作相关的函数实现，这些底层驱动函数将大量地在工程文件和功能包文件中被调用。

换句话说，当我们想将OpenRE移植到自己的电路板上时，我们只要完成好主控描述文件的编写，让其对外暴露的API与原先的一致，就不需要对工程文件夹和功能包文件夹做任何修改，OpenRE也就成功移植到第三方主控了。

接下来我们详细剖析一下主控描述文件（1_Processor），主要包含三部分：

* BoardAbstract：

 包含一个board_abstract父类和board子类。board_abstract类是顶层的板级抽象类，它留出了所有对电路板操作的API接口，但是考虑到不同的板子硬件设计不一样，所以在某些可能出现不同的地方，我们使用了虚函数，再用每块板子对应的board子类去继承board_abstract类并将虚函数具体实现。

 每一块板子都将有一个control_unit_xxx.cpp（也就是board子类具体实现的地方）与之对应，这些cpp文件种包含了led初始化、蜂鸣器初始化、电机接口初始化、电机使能失能、ADC初始化等。大家可以发现，这些操作都需要与具体的电路板的硬件设计所对应，比如LED具体对应哪个IO口，这是因板而异的，所以我们需要在子类去对应着实现。

 值得注意的是不同的control_unit_xxx.cpp都使用的同一个board.h头文件，这就保证了对外API接口的一致，至于在某工程中到底是哪个control_unit_xxx.cpp与board.h关联起来，取决于board.mk的编写，感兴趣的可以往上翻到* 4.2Makefile * 详解再看一下。

* Interupt：

 这部分就是中断处理函数的描述，应该不需要做修改。

 6个串口中断函数（F1的话是5个）不断的将串口收到的数据压入各自的队列；

 一个主中断函数，不断的在计时，用于while(1)中的分频操作；

 一个异常中断，单片机发生异常后会在这里利用蜂鸣器报警。

* STM32F4/STM32F1：

  这里面使我们编写好的BSPLIB，里面把单片机各种底层功能都打包实现了，可以直接调用。

  由于确定型号的单片机的IO的资源都是固定的，比如F1的串口1在没有重映射的情况下一直都是PA9、PA10，所以该部分文件也不需要改动。

综上所述，移植OpenRE到第三方主控的流程如下：
1. 新建一个control_unit_xxx.cpp（xxx是你的电路板的名称）。
2. 仿照着现有的control_unit_v2.cpp将所有函数按照你的电路板的特性实现好。函数名不要变，要和board.h能对应起来。
3. 修改board.mk，添加你的电路板的信息如下：
 >ifeq "$(strip $(BOARD_TYPE))" "control_unit_xxx"

 >DDEFS           += -DCONTROL_UNIT_XXX -DSTM32F10X

 >DDEFS           += -DHSE_VALUE=8000000 -DUSE_STDPERIPH_DRIVER

 >MCU             ?= cortex-m3

 >CPU_TYPE        ?= STM32F1

 >BOARD_ABSTRACT += $(TOP_PATH)/1_Processor/BoardAbstract/control_unit_xxx.cpp

 >endif
 *其中的，MCU、CPU_TYPE和“-DSTM32F10X”需要根据你使用的芯片情况改动。*

4. 在system_para.mk文件里添加你的电路板的硬件资源分配信息：
 >ifeq "$(strip $(BOARD_TYPE))" "control_unit_xxx"  

 >DEBUG_PRINTF_INTERFACE ?= usart_interface_4

 >PC_INTERFACE ?= usart_interface_1

 >RADIO_INTERFACE ?= usart_interface_4

 >endif

 *三个参数分别是，debug通信口、pc端和主控通信口、遥控器通信口。你只需要根据自己电路板的硬件资源分配来填写就好。*
5. 在工程文件夹的Makefile里面修改第一行：
 >BOARD_TYPE		?= control_unit_xxx

### 重要功能包讲解
在本小结，我们将单独拎出几个比较重要的软件功能包做一个比较细致的讲解，方便大家了解并学习一些重要功能的实现方法。

* common：

 该功能包包含了两部分文件，一个是调试接口的printf重映射，用于将printf信息打印到串口调试助手上。还有一个是接收消息的队列实现queue.cpp。我们为每一个串口都创建了一个队列用于接收消息，发送过来的数据会在串口中断处理函数里被压入队列。在程序的其他进程中，读取队列中的数据进行处理。

* hf_link:

 由于hf_link较为繁琐，我们放在第六章系统讲解。

* motor：

 该功能包包含电机控制代码motor_control和motor_top。

 motor_control中最重要的是pidOrdinaryCall函数和pidSeriesCall函数。

 同时我们还创建了motor_control类，实现了通用的PID控制函数，也留出了与具体电路板设计有关的电机初始化，使能等虚拟函数接口，在其子类DC_motor类中具体实现。

 * pidOrdinaryCall：该函数是单级PID函数，输入参数按顺序包括期望的总里程、实际测量总里程、单位时间内期望里程和单位时间内实际测量里程。函数的输出则是提供给电机的PWM值。
 * PidSeriesCall：串级PID，感兴趣的同学可以自己去看源码扒一扒，目前我们使用的是单级PID，效果已经可以达到控制的要求了。
 * motor_top中包含了电机的初始化函数、控制回调函数和电机测试函数。同时我们定义了两个类，一个是直流电机类DC_motor，它继承了motor_control类，将motor_control类中的虚函数具体实现了一下。DC_motor可以看作是对某个具体电机所建立的对象，motor_top类则是将机器人所使用的电机建立一个群组对象，实现对所有电机的统一管理。
 * motorTopInit：电机初始化函数，输入包括初始化电机的个数、PID控制周期、电机参数和仿真模式使能。
 * motorTopCall：该函数将在While(1)中以固定频率调用，实现对机器人底盘所有电机的控制。
 * motorTest：该函数在通常只在电机调试的时候使用，换句话说是内部人员开发的时候测试电机用的。使用方法是将其和motorTopCall放在一起，并屏蔽掉main.c内部的robot_control_p->call();函数。


* robot_control：

 该功能包包含四部分，分别是机器人的手臂、底盘、云台（头）和机器人的总体控制。

 Chassis（底盘）部分，构建了一个底盘类，主要实现了底盘的参数设置，底盘运动的相关数据解算。
 * setParameters：设置底盘的相关参数，包括底盘的型号、尺寸大小等。这里有个很关键的思想，我们定义了一个父类的TF_robot类，实现机器人速度和电机速度的转换，针对不同的地盘结构，有不同的子类去继承该父类，将父类的速度转换函数实例化。所以这边我们构造了一个父类对象，再根据机器人的底盘型号指向不同的子类，实现代码的封装。
 * Init：初始化底盘，其实就是调用了上面的函数。
 * updataGlobalSpeed：将机器人全局速度解算成各个轮子的速度。
 * updataRobotSpeed：将机器人坐标系速度解算成各个轮子的速度。
 * call：底盘控制回调函数，根据编码器数据解算里程。

 robot_control（机器人总体控制）部分，我们实现了一个机器人控制类，面向的是整个机器人，在统筹手臂、云台（头）和底盘的控制的同时，还负责了hf_link的响应。其中最重要的函数是call和hfLinkNodeEvent。
 * call：机器人控制回调函数，内部运行了hf_link响应函数和机器人三个部分（手臂、头和底盘）的控制回调函数。该函数在while(1)中以固定频率调用，实现对机器人的控制。
 * hfLinkNodeEvent：hf_link响应函数。当hf_link将机器人某些数据或参数更新之后，需要做出一些响应。比如hf_link更新了机器人的全局坐标速度之后, receive_package_renew[SET_GLOBAL_SPEED]标志位就会置1，一旦检测到该位的变化，则调用chassis.updataGlobalSpeed();将全局速度解算成每个电机的速度，实现机器人的移动。
