## HFLink详解
该功能包包含了两个类：StateMachine类和HFLink类。

* 通信协议：

 0XFF 0xFF sender_id receiver_id length_H length_L ****（data） check_sum
 StateMachine类中定义了一个HFMessage结构体，该结构体描述了一个数据包的信息：前两个0xFF是包头，后面是发送者id、接受者id、有用数据长度和数据内容存放数组（容量最大为120字节），最后一位则是校验位，使用的是和校验，check_sum= (0XFF + 0XFF+......)%255。

StateMachine类最重要的是状态机接收函数*StateMachine::receiveStates*和*StateMachine::sendMessage*函数。

* StateMachine::receiveStates(const unsigned char rx_data)：

 该函数会在程序中被循环调用，每次调用，都会将从串口接收消息队列中取出的最新的一个字节的数据传输到函数内部。每次只要传入的数据符合当前状态的要求，状态变量就会自动改变为下一状态，当程序顺利遍历完一遍所有状态之后，预示着收到一个完整可用的数据包，这时候该函数返回1（否则返回0），提示hf_link.cpp中的数据分析函数byteAnalysisCall可以开始进行数据分析。

* StateMachine::sendMessage(constHFMessage* tx_message_)：

 与状态机接收函数相反，该函数是将我们需要上传的数据进行打包发送，确保能够通过上位机的状态机接收函数。该函数的输入参数就是指向待发送数据包的HFMessage类型的指针。

HFLink类继承了StateMachine类，为了使用StateMachine类中的状态机接收函数和数据包发送函数。

同时，在HFLink类中，我们定义了Command枚举变量，里面都是指令类型，在解析数据包的时候，需要根据不同的指令类型做不同处理。

除此之外，因为PC端和主控端共用hflink代码，所以我们使用char型变量hf_link_node_model来区分上下位机（0 slave , 1 master）。

接下来我们来详解HFLink中的函数实现。在这里不贴代码大家可以打开文件hf_link.cpp对照查看。

* HFLink::byteAnalysisCall(const unsigned char rx_byte)：

 该函数会在while(1)中不断被调用，第一条if判断语句一旦判断正确，预示着状态机接收到一条完整的数据包。接着，会调用HFLink::packageAnalysis进行数据处理。
* HFLink::packageAnalysis(void)：

 第一次通信前需要上下位机握手，类似于一次通信尝试，告诉对方接下来要开始通信了。下位机调用该函数 *sendStruct(SHAKING_HANDS  , NULL , 0);* 向上位机发送握手请求，上位机收到握手请求后会向下给出答应，下位机收到应答后将shaking_hands_state标志位置1。握手成功。

 接下来开始正常通信。

 首先，根据状态机中获得的数据包的第一位数据确定指令的类型，指令的类型定义在一个枚举体中：
>command_state_ = (Command)rx_message.data[0];

 接着利用switch语句，针对不同的指令类型调用不同的数据处理函数。

 数据处理函数主要是两个，*setCommandAnalysis* 和 *readCommandAnalysis。*
* setCommandAnalysis：

 赋值指令分析函数。将上位机发过来的用于设置下位机某些参数或者变量的数据，通过memcpy函数，赋值给下位机对应的变量或参数。

* readCommandAnalysis：

 信息请求指令分析函数。收到上位机的数据请求消息之后，将下位机的某些变量或者参数，用memcpy函数拆分为多个字节的数据，打包发送给上位机。

* HFLink::sendStruct(const Command command_type , unsigned char* p ,  unsigned short intlen)：

 消息发送函数。传入参数包括：指令类别、指向发送内容首地址的指针和发送数据的长度。函数内部主要是填充了HFMessage类型数据的相关信息，但是要注意，每条指令都有自己的有效周期，也就是说，要以一定的频率给机器人发送指令。

## 如何自定义通信指令
首先，明确自定义通信指令的作用，涉及到的数据，并且根据通信指令的作用给自己的这条通信指令起个名字。

接着，在hf_link.h中，将该通信指令的名称添加到LAST_COMMAND_FLAG之前。

之后，在hf_link.cpp文件中找到HFLink::packageAnalysis(void)函数，在switch函数里面，仿照之前通信的格式添加新的通信指令解析内容。对于上下位机来讲，都是调用两个函数，setCommandAnalysis和readCommandAnalysis，这两个函数传入的参数都是三个，第一个指令类型，这个不需要自己改，因为是从更外面的函数传进来的，第二个是指向本条通信所涉及到的数据的指针，也就是相关数据的首地址，第三个是数据长度，用sizeof函数就好。如果本条指令不涉及到参数的传递（只是单纯的动作执行指令），就使用NULL指针，数据长度为0。

##多机支持
所有通信节点都有一个自己的ID，这也是为多机提供基础。多机很直观，就是多个机器人，多个控制终端之间的互相通信，通过ID号来一一对应。
ID其实就是一个单字节的数据，不过RoboLink有规定，主机和从机的ID范围是不一样的，这也是为了统一编排ID，提升效率。
主机（终端）概念：给实体机械人发送指令的的终端如遥控器，PC ，手机PP应用等 ，ID范围为0X01 - 0X10共15个ID。
从机概念：一个实体机器人（被控体）即为一个从机，比如移动机器人，平衡车，四轴 ，ID范围为 0X11 - 0X40  共48个ID。
广播ID：0XFF。


