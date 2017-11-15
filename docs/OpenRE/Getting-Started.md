## OpenRE环境配置
 
关于工具链的配置有两种方式，可以直接用apt-get 安装，如果网速太慢也可以在百度云下载deb包安装。

### Method1: 
```
sudo add-apt-repository ppa:terry.guo/gcc-arm-embedded  
sudo apt-get update          
sudo apt-get install openocd  gcc-arm-none-eabi    
sudo usermod -a -G dialout $USER    
sudo apt-get install lib32ncurses5 libtool libusb-1.0 libftdi-dev python python-serial python-empy libpython2.7:i386    
sudo apt-get remove modemmanager    
```

### Method2:(recommended)
- get toolchain it in [Development_Toolchain](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F3_Software%2FEmbedded_Development_Toolchain&parentPath=%2FHANDSFREE)
- put these softwares in OpenRE/5_Development_Toolchain     
- open a terminal and run:     

```
 cd 5_Development_Toolchain 
 tar -jxvf gcc-arm-none-eabi-5_4-2016q2.tar.bz2
 tar -jxvf openocd.tar.bz2
 tar -jxvf stlink.tar.bz2
 cd openocd/
 ./configure
 make clean
 make
 cd ../stlink/
 make clean
 make
 cd ../
 sudo usermod -a -G dialout $USER   
 sudo apt-get install lib32ncurses5 libtool libusb-1.0 libftdi-dev python python-serial python-empy libpython2.7:i386  
 sudo apt-get remove modemmanager    
```

### 代码编译与烧写预备
用jlink烧写时，由于不同的电路板外部晶振频率可能不一样，所以把A板的固件烧到B板就可能导致死机和锁死，然后下一次烧写的时候就烧不进了，当出现这种情况的时候，方法就是按下板子的复位键(按住不动)，运行烧写指令，一两秒后，松开复位键，就能烧写进去了。

为了确保你不会烧写错误，你先确保每个工程的makefile文件和你的板子是匹配的。这里先介绍每个工程所独有的makefile，下一篇会详细介绍整个库的makefile。

![makefile shotcut](/images/OpenRE/makefile.png)

白色字体是变量，黄色字体是变量值，注释部分是变量的可选值。接下来介绍每一个变量的含义。
* BOARD_TYPE：电路板型号，可选值是HANDSFREE生产的几款电路板（目前是3款，control_unit_mini、control_unit_v1和control_unit_v2）。
* ROBOT_MODEL：是当前使用的机器人的型号，可选值是HANDSFREE发布的几款机器人，（目前是三款，null、jilong、jilong_omni3和stone，null代表无机器人对象，在跑OpenRE简单测试程序的时候使用）。
* ROBOT_SIMULATION_MODE：仿真模式使能，如果enable，将不需要实体机器人，我们在电路板内部虚拟电机的存在。一般情况下都选择disable。
* BOOTLOADER_MODE：BOOTLOADER模式可以让用户直接从串口下载程序，如果disable就需要用jlink下载。目前默认disable。
* PAKG：代表本程序所需要使用到的功能包，在简单测试代码里，只用到了common包。在机器人实现代码里，用到了就相对较多了。如果不是自己开发程序，该部分内容一般不做修改。
* OS_MODULE：操作系统的模式，目前支持UCOSII、UCOSIII。如果裸跑单片机程序，就空着不填。
* THIRDPARTY_MODULE：第三方库的选择，比如矩阵库之类的，如果使用就在这里填上对应的第三方库名称。
在正式烧写前，请确保你之前的makefile都配置对了，主要是ROBOT_MODEL，BOARD_TYPE，BOOTLOADER_MODE这三个变量。

### 烧写一个流水灯的代码测试

> cd OpenRE/0_Project/examples/handsfree_simple_app/linux
* 把makefile的BOARD_TYPE改成你板子的型号，如果你使用不是HandsFree的官方控制器，则需要看懂makefile，看后面的配置是不是符合你自己的板子。
* 插上jlink同时用usb为板子供电。
* 接着编译：
> make
* 最后烧录：
> make burn

烧写成功的现象是，板子上的led灯持续闪烁。

如果使用的是STLink,则需要在make burn之前更改0_Project/makefile/flash.mk
如下:

```
ifeq "$(strip $(BOOTLOADER_MODE))" "enable"
BURN_TYPE       	= usbttl_bootloader_upload 
else
# (stlink/swd/jlink)_(stlink/openocd)_flash  "device"_"driver"_flash
BURN_TYPE      	 	= swd_openocd_flash
DEBUG_TYPE		= swd_openocd_debug
ERASE_TYPE		= swd_openocd_erase
endif
```
改成:

```
ifeq "$(strip $(BOOTLOADER_MODE))" "enable"
BURN_TYPE       	= usbttl_bootloader_upload 
else
# (stlink/swd/jlink)_(stlink/openocd)_flash  "device"_"driver"_flash
BURN_TYPE      	 	= stlink_openocd_flash
DEBUG_TYPE		= stlink_openocd_debug
ERASE_TYPE		= stlink_openocd_erase
endif
```

*（注：如果是重复烧录同一份代码，从第二遍开始就可以省去make clean和make步骤，直接make burn。但是如果两次烧录之间，有.h头文件被修改，就要先make clean，再make，最终make burn。）*

### 烧写机器的固件程序

固件程序有两个版本的,分别是有操作系统版和裸机版本的,裸机版本是稳定版,操作系统版经过测试也是可以正常使用的.如果你不懂,那么推荐使用裸机版本.

裸机版: 0_Project/firmware/handsfree_wheel_robot     
操作系统版: 0_Project/firmware/handsfree_wheel_robot_ucosIII     

烧写方法和上面一样,值得注意的是,要首先更改Makefile,选择不同的机器人与主控的方式

主要就是修改如下两个变量:

```
#####BOARD_TYPE: control_unit_mini control_unit_v2
BOARD_TYPE		?= control_unit_v2
#####ROBOT_MODEL : null stone stone_omni3 giraffe   
ROBOT_MODEL     ?= stone
```

一个是选择电路板的型号，一个是选择机器人的型号。可选项在makefile里面都以注释的形式标示出来了。    
Stone, Stone Omni3 , Giraffe机器人平台使用的是control_unit_v2控制器, Mini机器人使用的是control_unit_mini.     

这两个变量是必须要选对的,否则会出现意外,比如死锁控制器,或者烧错机器人的代码,导致运动控制不正常.

*（注：非嵌入式开发者只需看到这里即可，想深入开发OpenRE的可以继续研究后面的OpenRE教程）*
