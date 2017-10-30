## 串口USB插拔损坏解决方案
OpenRE的灵活性之一体现在对硬件资源的快速简单配置。我们的主控板除了串口一作为HFLink通信的默认端口外还预留了其他的串口。如果串口USB插拔损坏，则表示串口一的硬件损坏，此时可以转而使用其他未被占用的预留串口。

具体步骤如下：
### 如果使用的是control_unit_v2：
1.进入文件夹.../OpenRE/0_Project/makefile路径下，打开*system_para.mk*文件。

2.找到如下代码：
>ifeq "$(strip $(BOARD_TYPE))" "control_unit_v2"

>####select the usartx for board debug info printf : usart_interface_x,usb_slave  
DEBUG_PRINTF_INTERFACE ?= usart_interface_1

>####select the usartxfor pc communications (hf_link) :usart_interface_x,usb_slave  
PC_INTERFACE ?= usart_interface_1

>####select the usartx for remote control (hf_link) : usart_interface_x  
RADIO_INTERFACE ?= usart_interface_4
endif

*"DEBUG_PRINTF_INTERFACE"*就是调试使用的串口号，目前是串口1。

*"PC_INTERFACE"*就是HFLink，也即上下位机通信使用的串口号，目前也是串口1。

串口USB插拔损坏，表示串口一现在无法正常使用。只需要在这里将
>DEBUG_PRINTF_INTERFACE ?= usart_interface_1

>PC_INTERFACE ?= usart_interface_1

修改为

>DEBUG_PRINTF_INTERFACE ?= usart_interface_6

>PC_INTERFACE ?= usart_interface_6

即可。
#### 注意：串口2被SBUS占用，V2主控板上只剩下串口6空闲。

3.将USB的一端连接电脑，另一端，用我们淘宝店售卖的USB转TTL转接板接到V2主控板正面的uart6端口上。此时即可正常通信

-----------------------------------------

### 如果使用的是control_unit_mini：
1.进入文件夹.../OpenRE/0_Project/makefile路径下，打开*system_para.mk*文件。

2.找到如下代码：
>ifeq "$(strip $(BOARD_TYPE))" "control_unit_mini"

>####select the usartx for board debug info printf : usart_interface_x,usb_slave  
DEBUG_PRINTF_INTERFACE ?= usart_interface_4

>####select the usartxfor pc communications (hf_link) : usart_interface_x,usb_slave  
PC_INTERFACE ?= usart_interface_4

>####select the usartx for remote control (hf_link) : usart_interface_x  
RADIO_INTERFACE ?= usart_interface_5
endif

*DEBUG_PRINTF_INTERFACE*就是调试使用的串口号，目前是串口4。

*PC_INTERFACE*就是HFLink，也即上下位机通信使用的串口号，目前是串口1。

串口USB插拔损坏，表示串口一现在无法正常使用。只需要在这里将
>DEBUG_PRINTF_INTERFACE ?= usart_interface_4

>PC_INTERFACE ?= usart_interface_4

修改为

>DEBUG_PRINTF_INTERFACE ?= usart_interface_5

>PC_INTERFACE ?= usart_interface_5

即可。

3.将USB的一端连接电脑，另一端，用我们淘宝店售卖的USB转TTL转接板接到Mini主控板正面的usart4端口上。此时即可正常通信。
