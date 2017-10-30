## 第四章 架构介绍
### Makefile详解
每个工程都有一个自己的makefile文件（已经在上文讲解过），并且都include了顶层目录下的compiler_config.mk，而compiler_config.mk文件又包含了其它的.mk文件。

这里主要介绍以下几个重要的.mk文件，看懂这几个文件，自己DIY就完全不是问题。
* compiler_config.mk:

 这个文件除了去包含其它几个.mk之外，还定义了编译的规则，一句话来说，就是定义合适的规则，按照合适的编译流程，编译出.elf文件并且转化成可供烧录的.hex 和 .bin固件，懂makefile的应该是秒懂啦。

 重要代码：
 >ifeq "$(strip $(BOOTLOADER_MODE))" "enable"

 >DDEFS           += -DBOOTLOADER_ENABLE

 >endif

 *解析BootLoader使能情况，同时定义全局宏表征使能失能。*

 >ARMGCC		= $(TOP_PATH)/5_Development_Toolchain/gcc-arm-none-eabi-5_4-2016q2/bin/arm-none-eabi-gcc

 >ifeq ($(ARMGCC),$(wildcard $(ARMGCC)))

 >CCPREFIX	?= $(TOP_PATH)/5_Development_Toolchain/gcc-arm-none-eabi-5_4-2016q2/bin/arm-none-eabi-

 >else
 CCPREFIX	?= arm-none-eabi-

 >endif

 *在指定目录下寻找编译器，如果没有找到，就启用电脑里安装的编译器。主要是方便内部开发人员的，对大家来说可能没啥用。*
 >OPT += -O0

 *ARMGCC交叉编译的优化等级，可选参数为0、1、2、s建议在debug时候启用0级优化，这样能解决程序很多的潜在问题，编译成功之后启用s级优化，缩小编译后产生的文件大小。*

 >ifeq "$(strip $(CPU_TYPE))" "STM32F1"

 >FPU_STATE       == disable

 >endif

 >ifeq "$(strip $(CPU_TYPE))" "STM32F4"

 >FPU_STATE       == enable

 >endif

 >ifeq "$(strip $(FPU_STATE))" "enable"

 >OPT     += -mfloat-abi=hard

 >OPT     += -mfpu=fpv4-sp-d16

 >endif

 *根据芯片型号，决定是否启用FPU（浮点运算单元）。再根据是否使能FPU选择是否使用硬件浮点数等其他对应的编译选项。*

* system_para.mk:

 这个文件主要是电路板硬件资源分配的参数设置文件。目前主要就是解决通信端口的资源分配。

 >ifeq "$(strip $(BOARD_TYPE))" "control_unit_mini"

 >DEBUG_PRINTF_INTERFACE ?= usart_interface_4

 >PC_INTERFACE ?= usart_interface_1

 >RADIO_INTERFACE ?= usart_interface_4

 >endif

 *开头的三段代码是一个功能，就是根据当前电路板的型号（已经在顶层的makefile确定），设置具体的硬件资源分配，上面这段代码的含义是，用串口4作为debug的通信口，串口1作为pc端和主控板的通信口，串口4同时还作为主控与遥控器的通信口。*

 在这之后的内容，就是根据之前确定的参数，设置全局宏定义，传入到程序中去。

* board.mk：
 >ifeq "$(strip $(BOARD_TYPE))" "control_unit_mini"

 >DDEFS           += -DCONTROL_UNIT_MINI -DSTM32F10X

 >DDEFS           += -DHSE_VALUE=8000000 -DUSE_STDPERIPH_DRIVER

 >MCU             ?= cortex-m3

 >CPU_TYPE        ?= STM32F1

 >BOARD_ABSTRACT  += $(TOP_PATH)/1_Processor/BoardAbstract/control_unit_mini.cpp

 >endif

* package.mk
 >CXX_SRC+=$(foreachn,$(PAKG),$(wildcard$(PACKAGE_PATH)/$(n)/* .cpp))

 就是对makefile的PAKG变量进行解析，只要是依赖的包，就包含其源文件和路径。

###  基于OpenRE和HandsFree主控编写机器人程序

