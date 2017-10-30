## 概述
当你热爱某种事物，你可能会想办法去弥补它身上的缺点，即使意味着会牺牲你一点点，我们只是一群呆在大学里幼稚青年，但我们也有着对机器人事业的向往。     

HandsFree， 顾名思义解放双手。 我们想做到的是能够搭建一个共享的平台，一个友好的易于共同开发的框架。HandsFree 从嵌入式平台开始，逐步地扩展到了相应的其他周边，为的是让整个机器人的开发过程降低耦合，尽可能地减少一些底层的开发环节，在开发过程中提供了一个更好的交流方式。HandsFree 其理念核心是优化开发过程的同时，让设计的 idea 的分享过程更加 Free，是乐于分享的，鼓励分享的。     

HandsFree Team 是一个乐于奉献于机器人事业的团队，我们希望能为每一个走进机器人世界的学者带来便利。HandsFree 理念总结成一句话：创造一个机会共同成长。  
          
如果你觉得不错的话，就一起加入进来吧！！！     

## 理念：  
探索，成长，分享

## 宗旨：  
* 以学习和科研为第一要义，对知识和技术的追求永无止境，不断创新，精益求精，提升自我； 
* 其次，尽能力承担一定的社会责任，重视分享；
* 最后，鼓励创造社会价值和财富以维持长期发展。

## 内容：  
HandsFree 是一个面向机器人研究、开发的开源软硬件系统。她有完备与科学的框架， 以优秀的嵌入式系统框架为核心， 精良的电路、 机械设计为支撑，帮您快速实现多种形态的机器人。本系统包含机器人导航，SLAM，计算机视觉等模块， 并拥有自己上层软件和调试系统。 她支持国外其他的开源项目， 如 ROS,MPRT, PIXHAWK 等，这一切都为您带来了无比的便捷和快乐！

![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_001.jpg)
![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_002.jpg)

##  现状： 
HandsFree 是一个机器人开源项目，涵盖了和机器人相关的许多方面。我们面向开源的主要任务是搭建一个机器人系统， 并且尽可能使用各种工具来实现目的。       

HandsFree 人员由 **HandsFree Team** ， **HandsFree Community** 组成。      

**HandsFree Team** 是 HandsFree 的缔造者和主要开发人员，负责更新，管理，建设 HandsFree 开源社区。目前 HandsFree 团队主要是由西北工业大学，厦门大学等几所大学的学生或者实验室组成。         

**HandsFreeCommunity** ，指所有参与，使用该开源项目的伙伴构建的交流圈。
       
我们希望能有志同道合的人加入我们，一起学习交流。   

## HandsFree 组成
项目虽然看起来涉及很广，但目前主要任务大概有三个。      

### 一 OpenRE 库
全称 Open Source Robot Embedded Library，也就是机器人嵌入式库。简单的说，其作用与国外知名的无人机开发架构 pixhawk 类似，只不过 pixhwak 主要是面向飞行器，而 OpenRE 则是面向多模态机器人的。

![OpenRE](/images/OpenRE/Embedded_Architectural.jpg)

> [Download OpenRE](https://github.com/HANDS-FREE/OpenRE)
       
### 二 多模态平台设计
我们的开发项目和开发平台是多样化的，比如二轮，三轮的移动机器人，四旋翼固定翼飞行器等，重复造轮子的问题是机器人学者和创业者最常遇到的问题，好的系统是要求很好的泛性的，能够适应大部分平台，避免了重复劳动的弊端，这就要求我们的产品更加多元化。	在多模态机器人平台搭建方面，研究的主要内容是设计精良的机械和电路系统。机械系统包括各种模型的机器人躯体、机械臂、云台等。电路则包含控制系统，驱动电路，电源管理系统，硬件调试等方面。

![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_003.jpg)
![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_004.jpg)

**多模态平台旨在以机器人学，自动化，通信电子和周边知识为支撑，搭建科学、鲁棒、友好、统一的机器人硬件系统，以配合整个软硬件系统的统一**
- 为了促进社区交流，我们开源了大部分的设计资料，请看[百度云](https://pan.baidu.com/s/1nuSvs7Z#list/path=%2FHANDSFREE%2FHands_Free_Release%2F2_Hardware&parentPath=%2FHANDSFREE)
         
### 三 系统搭建
主要是基于前两个任务，结合团队在 SLAM， 物体识别，机器人任务规划等研究，以及国外知名的 ROS 等开源项目，搭建整个机器人系统，实现一些应用。
- 自主移动模块框架搭建
- 物体识别模块
- 机械臂控制模块
- 多机器人协同

[HandsFree Github](https://github.com/HANDS-FREE/handsfree)     

![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_009.jpg)
![Alt text](/images/About/HandsFree_Introduction/HandsFree_Introduction_2016_4_2_011.jpg)

### 总结
我们希望HandsFree 成为一套可以遵循的标准，而不仅仅只是一个工程，所以我们精心制定了电路设计标准和机械设计标准，并且公开了我们团队的PCBLIB和机械模型库，凡是照着这个标准来设计的机器人将会很大程度的兼容HandsFree的软件系统，我们希望此举让更多的机器人研究者得到便利，也希望有心人帮助我们完善这个标准的内容。

### PIL 介绍
西北工业大学布树辉教授的智能系统实验室开发的跨平台软件库 [PIL](https://github.com/HANDS-FREE/PIL )，支持多线程、时钟、插件、网络、常用硬件抽象、计算机视觉、GUI等功能。布老师是我人生中最敬佩导师，他不仅有着超强的工程和科研能力，而且和蔼可亲，亦师亦友，手把手教，更难得的是，他比学生们还要努力，总是走在团队的最前面带着每个学生奋斗，喜欢机器人或者无人机领域的伙伴们可以关注一下他的[个人网站](http://www.adv-ci.com/blog/)，如果想读他研究生或者博士的伙伴也可以来联系群主。   

